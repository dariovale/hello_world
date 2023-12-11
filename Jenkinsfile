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
                 echo 'build docker image...'     
                withEnv(['DOCKER_IMAGE_NAME=dariopiphelloworld','DOCKER_IMAGE_TAG=1.0'])
                {
                   sh 'docker build -t $DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG .' 
                }    
            }
        }
        
        
    }
}
