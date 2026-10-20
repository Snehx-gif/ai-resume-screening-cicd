
pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'snehaydv/ai-resume-screening'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Project Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Check Docker') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ai-resume-screening:cicd-v1 .'
                sh 'docker tag ai-resume-screening:cicd-v1 $DOCKER_IMAGE:cicd-v1'
            }
        }

        stage('Verify Docker Image') {
            steps {
                sh 'docker images'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_TOKEN'
                )]) {
                    sh '''
                        echo "$DOCKER_TOKEN" | docker login -u "$DOCKER_USER" --password-stdin
                        docker push "$DOCKER_IMAGE:cicd-v1"
                        docker logout
                    '''
                }
            }
        }
    }
}
