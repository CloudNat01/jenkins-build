pipeline{

	agent docker

	environment {
		DOCKERHUB_CREDENTIALS=credentials('cloudnat-dockerhub')
	}

	stages {
	    
	   stage('Build') {
               steps {
			sh 'docker build -t cloudnat/sample-web:latest .'
			}
		}

	   stage('Login') {
	       steps {
		       sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

	   stage('Push') {
             steps {
			sh 'docker push cloudnat/sample-web:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
