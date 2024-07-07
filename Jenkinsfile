pipeline {
    agent any

    environment {
        // Define environment variables if needed
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the merged-services branch from your repository
                git branch: 'merged-services', url: 'https://github.com/Abhijeet00116/multi-tier-microservice.git'
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend-service') {
                    // Build steps for frontend service
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir('backend-service') {
                    script {
                        sh 'mvn clean install'
                        sh 'mvn test'
                        sh 'mvn package'
                    }
                }
            }
        }

        stage('Build Database') {
            steps {
                dir('database-service') {
                    script {
                        // Assuming you might need to prepare something for the database service
                        // For example, preparing Docker images or other necessary steps
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy all services using Docker Compose
                    sh 'docker-compose -f database-service/docker-compose.yml up -d'
                }
            }
        }
    }

    post {
        success {
            echo 'All services deployed successfully!'
        }
        failure {
            echo 'Service deployment failed!'
        }
    }
}

