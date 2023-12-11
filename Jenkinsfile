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
        stage('Clone repository') {
            steps {
                echo 'cloning...'
                script {
                git credentialsId: 'afe2edbf-9b6c-4afc-aa6b-28bef61f7ef8', url: 'https://github.com/dariovale/hello_world.git'
                }
            }
            
        }

               stage('Build image') {
            steps {
                echo 'BUILDING IMAGE...'
                script {
                dockerImage = docker.build("darioalberto364@outlook.com/dariopiphelloworld:latest")
                }
            }
            
        }


                  stage('PUSH image') {
            steps {
                echo 'PUSHING IMAGE...'
                script {
               withDockerRegistry([ credentialsId: "203314de-f2e5-4e61-9d3e-db3e331cbde9", url: "" ]) {
        dockerImage.push()
        }
                }
            }
            
        }
        
    }
}
