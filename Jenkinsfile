pipeline {
    agent any
    environment {
        IMAGE = "sagar520/gitops-project:${BUILD_NUMBER}"
    }
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/MAJJISAGAR/gitops-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-creds') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
