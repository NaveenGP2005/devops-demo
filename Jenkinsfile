pipeline {
    agent any

    stages {
        
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/NaveenGP2005/devops-demo'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                echo "Building Docker Image..."
                docker build -t simple-webapp:latest .
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Deploying using Docker Compose..."
                docker-compose down || true
                docker-compose up -d --build
                '''
            }
        }
    }

    post {
        success {
            echo "Deployment Successful! 🚀"
        }
        failure {
            echo "Pipeline Failed ❌"
        }
    }
}
