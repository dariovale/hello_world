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
                git credentialsId: 'git', url: 'https://github.com/dariovale/hello_world.git'
                dockerImage = docker.build("v9lent1n9/dariopiphelloworld:latest")
                                withDockerRegistry([ credentialsId: "203314de-f2e5-4e61-9d3e-db3e331cbde9", url: "" ]) {
            dockerImage.push()
        }
                }
            }
            
        }
        
    }
}
