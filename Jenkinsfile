// Scripted Pipeline
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration Test"
// 	}
// }

// DECLERATIVE PIPELINE
pipeline {
	agent any
	stages {
		stage ('Build') {
			steps {
				echo "Build"
			}
		}
		stage ('Test') {
			steps {
				echo "Test"
			}		
		}
		stage ('Integration Teset') { 
			steps {
				echo "Integration Test"
			}			
		}
	} 
	
	post {
		always {
			echo 'I run always!'
		}
		success {
			echo 'I run only when you are Successful!'
		}
		failure {
			echo 'I run only when you Fail!'
		}
	}
}