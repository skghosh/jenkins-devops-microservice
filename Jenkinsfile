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
		stage{
			steps{
				echo "Build"
			}
			stage('Test') {
				echo "Test"
			}
			stage('Integration Test') {
				echo "Integration Test"
			}
		}
	}
}