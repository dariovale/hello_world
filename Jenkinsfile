#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root'
        }
    }

environment {
    DOCKERHUB_CREDENTIALS = credentials('203314de-f2e5-4e61-9d3e-db3e331cbde9')
  }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install'
                sh 'docker build -t v9lent1n9/dariopiphelloworld .'
            }
        }

stage('Login') {
      steps {
       sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }

         stage('Push') {
      steps {
        sh 'docker push v9lent1n9/dariopiphelloworld'
      }
    }


        
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test'
            }
        }       
        
    }
}
