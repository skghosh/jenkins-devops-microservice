// DECLERATIVE PIPELINE
pipeline {
	agent any
	// agent { 
	// 	docker { 
	// 		image 'maven:3-alpine' 
	// 		args '-v /root/.m2:/root/.m2'
	// 	} 
	// }

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
	}


	stages {
		stage ('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker --version'
				echo "PATH = $PATH"
				echo "BUILD NUMBER = $env.BUILD_NUMBER"
				echo "BUILD_ID = $env.BUILD_ID"
				echo "JOB_NAME = $env.JOB_NAME"
				echo "BUILD_URL = $env.BUILD_URL"
			}
		}
		stage ('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage ('Test') {
			steps {
				sh "mvn test"
			}		
		}
		stage ('Integration Teset') { 
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}			
		}
		stage ('Package') { 
			steps {
				sh "mvn package -DskipTests"
			}			
		}		
		stage ('Build Docker Image') { 
			steps {
				//"docker build -t sandeepkghosh/currency-exchange-devops:$env.BUILD_TAG"
				dockerImage = docker.build("sandeepkghosh/currency-exchange-devops:${env.BUILD_ID}")
				
			}			
		}
		
		stage ('Push Docker Image') { 
			steps {
				script{
					docker.withRegistry('https://hub.docker.com/', 'dockerhub_credential_id') {
						dockerImage.push()
						dockerImage.push('latest')
					}
				}
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