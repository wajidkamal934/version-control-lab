pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "myusername/my-app:latest"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/your-repository.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }
        stage('Test Docker Image') {
            steps {
                script {
                    sh 'docker run $DOCKER_IMAGE npm test'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                // Your deployment steps, e.g., deploy to AWS, GCP, etc.
                script {
                    sh 'deploy.sh'
                }
            }
        }
    }
}