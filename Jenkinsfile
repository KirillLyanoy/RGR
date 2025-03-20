pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/KirillLyanoy/RGR.git', branch: 'main'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop my-app || true' // Игнорировать ошибку, если контейнер не существует
                sh 'docker rm my-app || true'   // Игнорировать ошибку, если контейнер не существует
                sh 'docker network create app-network || true' // Создать сеть, если она ещё не существует
                sh 'docker run -d --name my-app --network app-network my-app:latest'
            }
        }
    }
}
