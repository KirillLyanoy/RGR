pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/KirillLyanoy/RGR'
            }
        }
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t rgr:latest .'
            }
        }
        stage('Deploy Docker Container') {
            steps {
                sh 'docker stop your-app || true'
                sh 'docker rm your-app || true'
                sh 'docker run -d --name your-app -p 8081:8081 rgr:latest'
            }
        }
    }
}
