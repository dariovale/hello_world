pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('203314de-f2e5-4e61-9d3e-db3e331cbde9')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t darioalberto364@outlook.com/dariopiphelloworld:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push darioalberto364@outlook.com/dariopiphelloworld:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
