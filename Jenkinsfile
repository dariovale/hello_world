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
        git credentialsId: 'git', url: 'https://github.com/dariovale/hello_world.git'
    }

 stage('Build image') {
       dockerImage = docker.build("v9lent1n9/dariopiphelloworld:latest")
    }
stage('Push image') {
        withDockerRegistry([ credentialsId: "203314de-f2e5-4e61-9d3e-db3e331cbde9", url: "" ]) {
        dockerImage.push()
        }
    }    
        
        
        
    }
}
