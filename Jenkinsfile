pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t eaglehaslanded/python:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $env.DOCKERHUB_CREDENTIALS_PSW | docker login -u $env.DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push eaglehaslanded/python:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}