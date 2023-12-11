#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root'
        }

        
        node {   
    stage('Clone repository') {
        git credentialsId: 'git', url: 'https://github.com/Monishamacharla/reactapp'
    }
    
    stage('Build image') {
       dockerImage = docker.build("monishavasu/my-react-app:latest")
    }
    
 stage('Push image') {
        withDockerRegistry([ credentialsId: "dockerhubaccount", url: "" ]) {
        dockerImage.push()
        }
    }    
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
        
    }
}
