#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root'
        }
       
    }  
    environment {
            registry = "YourDockerhubAccount/YourRepository"
            registryCredential = '203314de-f2e5-4e61-9d3e-db3e331cbde9'
                dockerImage = ''
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

        stage('Cloning our Git') {
                steps {
                        git 'https://github.com/YourGithubAccount/YourGithubRepository.git'
                    }
                }
        

stage('CREATE DOCKER IMG') {
            steps {
                echo 'CREATING IMG...'
              sh 'docker build -t v9lent1n9/dariopiphelloworld .'
            }
        } 
        
        
    }
}
