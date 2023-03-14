 pipeline {
   
   agent any
   
   options {

     buildDiscarder(logRotator(numToKeepStr: '5'))
   }
  
   environment {

     DOCKERHUB_CREDENTIALS = credentials('dockerhub')
   }

   stages {

     stage('Build') {

        steps {

          sh 'docker build -t mangisettisampath66@gmail.com/dp-alpine:latest .'
        }
      }
      stage('login') {

        steps {
     
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
         }
       }
       stage('push') {
         
         steps {

            sh 'docker push mangisettisampath66@gmail.com/dp-alpine:latest'
         }
       }
     }
     post {

       always {

         sh 'docker logout'
        }
      }
    }
