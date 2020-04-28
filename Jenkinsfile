pipeline {
	agent any
	environment {
		dockerHome = tool 'CICDdocker'
		mavenHome = tool 'maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Build'){
			steps {
				sh 'mvn --version'
				sh 'docker -version'
				echo "Build"
				echo "$PATH"
				echo "$env.BUILD_TAG"
			}	
		}
		
		stage('Test'){
			steps {
				echo "Test"
		}	}
		
		stage('Integration'){
			steps {
				echo "Integration"
			}
		}
	}
	post {
	always {
		echo 'I am awesom. I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}
