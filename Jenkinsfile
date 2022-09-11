pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dhub_creds')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t sathyadevops/k8example:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sathyadevops/k8example:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
