pipeline{
agent any
	tools {
maven 'maven'	
	}
	stages{
		stage('git checkout'){
			steps{
			git 'https://github.com/janardhan1234567/maven-web-application.git'
			}
		}	
		stage('sonar analysis'){
		
			steps{
			sh 'mvn sonar:sonar'
			}	
		}
		stage('generate war'){
			steps{
			sh 'mvn clean package'
			}
		}
		stage('publish war'){
			steps{
			sh 'mvn deploy'
			}
		}
		stage('deploy in container'){
			steps{
				sshagent(['tomcatmaster']){
				sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@54.146.228.8:/opt/tomcat/webapps/'
				}
				
			}
		}	
	
	}	
}
