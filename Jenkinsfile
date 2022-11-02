pipeline{

	agent any

	stages {
	    stage('gitclone') {
			steps {
				git 'https://github.com/CloudNat01/jenkins-build.git'
			}
		}

	    stage('Build') {
			steps {
				sh 'docker build -t cloudnat/jk-img:latest .'
			}
		}

	     stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_TOKEN | docker login -u $DOCKERHUB_USERNAME --password-stdin'
			}
		}
	     stage('Push') {
			steps {
				sh 'docker push cloudnat/jk-img:latest'
			}
		}
	}
	post {
		always {
			sh 'docker logout'
		}
	}

}

