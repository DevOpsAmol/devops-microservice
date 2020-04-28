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
		
		stage('Package'){
			steps {
				sh 'mvn package -DskipTests'
			}
		}
		
		stage('Build Docker Image'){
			steps {
				//"docker build -t akadam88/devops-microservice:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("akadam88/devops-microservice:${env.BUILD_TAG}")
				}
			}
		}
		
		stage('Push Docker Image'){
			steps {
				
				script {
						docker.withRegistry('', 'dockerhub') {
							dockerImage.push();
							dockerImage.psuh('latest');
						}
					
				}
				
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
