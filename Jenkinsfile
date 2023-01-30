pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhublogin')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t vineetv36/k8s-web-to-nginx:4.0 .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}


		stage('Push') {

			steps {
				sh 'docker push vineetv36/k8s-web-to-nginx:4.0'
			}
		}

	}

	post {
		always {
			sh 'docker logout'
		}
	}

}