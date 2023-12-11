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

    stage('Deploy') {
            steps {
                echo 'DEPLOYING...'
                // Specify the Docker Hub registry
                docker.withRegistry('', '203314de-f2e5-4e61-9d3e-db3e331cbde9') {
                    // Tag the Docker image with the Docker Hub username
                    sh 'docker tag my-app darioalberto364@outlook.com/my-app'

                    // Push the Docker image to the Docker Hub registry
                    sh 'docker push darioalberto364@outlook.com/my-app'
                }
            }
        
        
    }
}
