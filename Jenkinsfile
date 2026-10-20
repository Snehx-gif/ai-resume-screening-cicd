pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Project Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t ai-resume-screening:cicd-v1 .'
            }
        }
    }
}