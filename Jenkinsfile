pipeline{
    stages{
        stage('checkout'){
            steps{
                git url: 'https://github.com/Aryangupta6612/Practice_ci-cd.git', branch: 'master'
            }
        }
        stage('build and deploy'){
            steps{
                sh '''
                    echo "removing unnecessary files"
                    
                    docker-compose down||true
                    docker-compose up -d --build
                '''
            }
        }
    }
    post{
        always{
            sh 'docker compose prune -f||true'
            sh 'docker image prune -f||true'
        }
        success{
            echo "Build and deploy successful"
        }
        failure{
            echo "Build and deploy failed"
        }
    }
}