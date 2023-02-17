pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
				sh 'mvn clean install'
				echo 'build stage succesful'
			}
		}
		stage('Test'){
			steps{
				sh 'mvn clean test'
				echo 'test stage succesful'
				
				post{
					always{
						junit 'target/surefire-reports/*.xml'
					}
				}
			}
			
		}
		stage('Deploy'){
			steps{
				sh 'mvn clean deploy'
				echo 'deploy stage succesful'
			}
		}
	}
	
	post{
	
		failure{
			echo 'Pipeline failed'
			}
		}
}		
