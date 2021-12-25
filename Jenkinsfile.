pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-hub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/CloudNat01/jenkins-build/'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t lovetha/sample-web:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push lovetha/sample-web:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
