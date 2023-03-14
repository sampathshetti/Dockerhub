 pipeline {
   
   agent any
   
   options {

     buildDiscarder(logRotator(numToKeepStr: '5'))
   }
  
   environment {

     DOCKERHUB_CREDENTIALS = credentials('sampath-dockerhub')
   }

   stages {

     stage('Build') {

        steps {

          sh 'docker build -t sampath/dp-alpine:latest .'
        }
      }
      stage('login') {

        steps {
     
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-sampath@1914'
         }
       }
       stage('push') {
         
         steps {

            sh 'docker push sampath/dp-alpine:latest'
         }
       }
     }
     post {

       always {

         sh 'docker logout'
        }
      }
    }
