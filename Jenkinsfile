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
