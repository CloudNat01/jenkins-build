pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('cloudnat-dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/CloudNat01/jenkins-build.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t cloudnat/sample:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push cloudnat/sample:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
