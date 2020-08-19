pipeline{

	agent any
	
	stages {
	
		stage('Build') {
			steps {
				sh 'git submodule mvn clean package'
			}
		}
		
		stage('Deploy') {
			steps {
				withCredentials([[
								$class				: 'UsernamePasswordMultiBinding',
								credentialsId		: 'PCF_LOGIN',
								usernameVariable	: 'USERNAME',
								passwordVariable	: 'PASSWORD']]) {
						
					sh 'C:/Program Files/Cloud Foundry/cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'									
					sh 'C:/Program Files/Cloud Foundry/cf push'
				}
			}
		}
	}



}