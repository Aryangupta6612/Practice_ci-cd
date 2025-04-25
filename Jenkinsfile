pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Aryangupta6612/Practice_ci-cd.git', branch: 'master'
            }
        }

        stage('Build and Deploy') {
            steps {
                sh '''
                    echo "Removing unnecessary containers (if any)"
                    docker compose down || true

                    echo "Building and starting containers"
                    docker compose up -d --build
                '''
            }
        }
    }

    post {
        always {
            echo "Cleaning up unused resources"
            sh 'docker compose down || true'
            sh 'docker system prune -f || true'
        }

        success {
            echo "✅ Build and deploy successful"
        }

        failure {
            echo "❌ Build and deploy failed"
        }
    }
}
