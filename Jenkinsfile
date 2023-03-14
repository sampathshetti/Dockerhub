 pipeline {
   
   agent any
   
   options {

     buildDiscarder(logRotator(numToKeepStr: '5'))
   }
  
   environment {

     DOCKERHUB_CREDENTIALS = credentials('sampathshetti-dockerhub')
   }

   stages {

     stage('Build') {

        steps {

          sh 'docker build -t sampathshetti/dp-alpine:latest .'
        }
      }
      stage('login') {

        steps {
     
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
         }
       }
       stage('push') {
         
         steps {

            sh 'docker push sampathshetti/dp-alpine:latest'
         }
       }
     }
     post {

       always {

         sh 'docker logout'
        }
      }
    }
