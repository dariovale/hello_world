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
                        git 'https://github.com/dariovale/hello_world.git'
                    }
                }


        stage('Building our image') {
                steps{
                        script {
                            dockerImage = docker.build registry + ":$BUILD_NUMBER"
                                }
                        }
                }

        stage('Deploy our image') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                        }
                    }
                }
             }
            stage('Cleaning up') {
                    steps{
                        sh "docker rmi $registry:$BUILD_NUMBER"
                        }
            }
        
        
        
    }
}
