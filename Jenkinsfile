// pipeline{

// 	agent any

// 	environment {
// 		DOCKERHUB_CREDENTIALS=credentials('cloudnat-dockerhub')
// 	}

// 	stages {
	    
// 	    stage('gitclone') {

// 			steps {
// 				git 'https://github.com/CloudNat01/jenkins-build.git'
// 			}
// 		}

// 		stage('Build') {

// 			steps {
// 				sh 'docker build -t cloudnat/sample:latest .'
// 			}
// 		}

// 		stage('Login') {

// 			steps {
// 				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
// 			}
// 		}

// 		stage('Push') {

// 			steps {
// 				sh 'docker push cloudnat/sample:latest'
// 			}
// 		}
// 	}

// 	post {
// 		always {
// 			sh 'docker logout'
// 		}
// 	}

// }

node {

    stage("Git Clone"){

        git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/CloudNat01/jenkins-build.git'
    }


    stage("Docker build"){
        sh 'docker version'
        sh 'docker build -t cloudnat/sample-image:demo-build .'
        sh 'docker image list'
    }

    withCredentials([string(credentialsId: 'cloudnat-dockerhub', variable: 'PASSWORD')]) {
        sh 'docker login -u cloudnat -p $PASSWORD'
    }

    stage("Push Image to Docker Hub"){
        sh 'docker push  cloudnat/sample-image:demo-build'
    }
}
 

