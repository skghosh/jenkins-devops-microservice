// DECLERATIVE PIPELINE
pipeline {
	agent any
	// agent { 
	// 	docker { 
	// 		image 'maven:3-alpine' 
	// 		args '-v /root/.m2:/root/.m2'
	// 	} 
	// }
	stages {
		stage ('Build') {
			steps {
				echo "Path = $PATH"
				echo "BUILD NUMBER = $env.BUILD_NUMBER"
				echo "BUILD_ID = $env.BUILD_ID"
				echo "JOB_NAME = $env.JOB_NAME"
				echo "BUILD_URL = $env.BUILD_URL"
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
		//changed
		//unstable
	}
}