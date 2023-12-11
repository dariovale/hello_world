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
                }
            }
            
        }
        
    }
}
