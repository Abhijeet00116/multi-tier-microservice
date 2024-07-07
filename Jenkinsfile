pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'backend-service', url: 'https://github.com/Abhijeet00116/multi-tier-microservice.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    sh 'mvn package'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'docker build -t backend-service:latest .'
                    sh 'docker run -d -p 8080:8080 backend-service:latest'
                }
            }
        }
    }

    post {
        success {
            echo 'Backend Service deployed successfully!'
        }
        failure {
            echo 'Backend Service deployment failed!'
        }
    }
}

