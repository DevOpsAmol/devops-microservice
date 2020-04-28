pipeline {
	agent any
	environment {
		dockerHome = tool 'CICDdocker'
		mavenHome = tool 'maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('variables'){
			steps {
				sh 'mvn --version'
				sh 'docker -version'
				echo "Build"
				echo "$PATH"
				echo "$env.BUILD_TAG"
			}	
		}
		
		stage('Compile'){
			steps {
				sh 'mvn clean compile'
			}	
		}
		
		stage('Test'){
			steps {
				sh 'mvn test'
			}	
		}
		
		stage('Integration'){
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
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
