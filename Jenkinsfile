#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root'
        }
       
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


stage('Build docker image') {
            steps {
                // Assuming the Dockerfile is in the same directory as the Jenkinsfile
                sh 'docker build -t dariopiphelloworld .'
            }
        }
        
        
    }
}
