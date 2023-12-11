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


stage('CREATE DOCKER IMG') {
            steps {
                echo 'CREATING IMG...'
              sh 'docker build -t dariopiphelloworld:1.0.0 .'
            }
        } 
        
        
    }
}
