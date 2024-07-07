pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'frontend-service', url: 'https://github.com/Abhijeet00116/multi-tier-microservice.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build steps, e.g., npm install if it's a JS frontend
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deployment steps, e.g., copy files to a web server
                }
            }
        }
    }

    post {
        success {
            echo 'Frontend Service deployed successfully!'
        }
        failure {
            echo 'Frontend Service deployment failed!'
        }
    }
}

