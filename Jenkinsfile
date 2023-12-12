node {
	def application = "springbootapp"
	def dockerhubaccountid = "darioalberto364@outlook.com"
	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
	}

}
