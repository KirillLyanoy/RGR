pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'docker build -t rgr .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'docker run rgr ./run-tests.sh'
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
