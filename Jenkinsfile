pipeline {
     agent any
 
     stages {
         stage('Checkout') {
             steps {
                 git branch: 'main',
                     url: 'https://github.com/KirillLyanoy/RGR',
                     credentialsId: 'bdc4046a-c3f2-47b0-a972-cbf9f15083ce'
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
