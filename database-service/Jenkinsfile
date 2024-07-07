pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'database-service', url: 'https://github.com/Abhijeet00116/multi-tier-microservice.git'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        success {
            echo 'Database Service deployed successfully!'
        }
        failure {
            echo 'Database Service deployment failed!'
        }
    }
}

