# jenkins-scripted-pipeline-example

pipeline {
	agent any
	stages {
		stage('Compile') {
			steps {
					echo "Compiled successfully!!";
			}
		}

		stage('JUnit') {
			steps {
					echo "JUnit Passed Successfully!";
			}
		}

		stage('Quality-Gate') {
			steps {
					echo "SonarQube Quality Gate Passed successfully!!";
					/*sh exit ("1");*/
			}
		}

		stage {
			steps {
					echo "Pass!";
			}
		}
	}
	post {
		always {
			echo 'This will always run'
		}
		success {
			echo 'This will run only if successful'
		}
		failure {
			echo 'This will run only if failed'
		}
		unstable {
			echo 'This will run only if the run was marked as unstable'
		}
		changed {
			echo 'This will run only if the stare of the Pipeline has changed'
			echo 'For example, if the Pipeline was previously failing but is now successfull'
		}
	}
}
