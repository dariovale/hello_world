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


        
stage('Push') {

    steps {

        // Replace 'DOCKER_HUB_CREDENTIALS' with the ID of your credentials in Jenkins

        withCredentials([usernamePassword(credentialsId: '203314de-f2e5-4e61-9d3e-db3e331cbde9', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {

            withEnv(['DOCKER_IMAGE_NAME=dariopiphelloworld-image', 'DOCKER_IMAGE_TAG=1.0']) {

                sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'

                sh 'docker tag $DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG $DOCKER_USERNAME/$DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG'

                sh 'docker push $DOCKER_USERNAME/$DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG'

            }

       }

    }

}
        
        
    }
}
