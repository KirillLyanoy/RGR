pipeline {
     agent any
 
     stages {
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
