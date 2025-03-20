pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/KirillLyanoy/RGR.git', branch: 'main'
            }
        }
        stage('Build Docker Image') {
            when {
                changeset "**/*" 
                not { changeset "Jenkinsfile" } 
            }
            steps {
                sh 'docker build -t my-app:latest .'
            }
        }
        stage('Deploy') {
            when {
                changeset "**/*" 
                not { changeset "Jenkinsfile" }
            }
            steps {
                sh 'docker stop my-app || true'
                sh 'docker rm my-app || true'
                sh 'docker network create app-network || true'
                sh 'docker run -d --name my-app --network app-network my-app:latest'
            }
        }
    }
}
