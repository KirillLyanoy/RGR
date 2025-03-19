pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/KirillLyanoy/RGR',
                    credentialsId: 'ac935320-22e6-421e-b058-48bf9380e360'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'docker build -t my-app .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'docker run my-app ./run-tests.sh'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'docker-compose down && docker-compose up -d'
            }
        }
    }
}
