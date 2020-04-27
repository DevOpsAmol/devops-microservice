pipeline {
	agent any
	stages {
		stage('Build'){
			steps {
				echo "Build"
				
		}	}
		
		stage('Test'){
			steps {
					echo "Test"
		}	}
		
		stage('Integration'){
			steps {
					echo "Integration"
		}	}
	} post {
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