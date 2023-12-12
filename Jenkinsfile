pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('203314de-f2e5-4e61-9d3e-db3e331cbde9')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t v9lent1n9/dariopiphelloworld:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push v9lent1n9/dariopiphelloworld:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
