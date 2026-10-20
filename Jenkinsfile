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
                sh 'ls -la'
            }
        }

        stage('Install Docker Check') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ai-resume-screening:cicd-v1 .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                sh 'docker images ai-resume-screening'
            }
        }
    }
}