pipeline {
	agent { label 'linux' }
	stages {
		stage ('build') {
			steps {
				sh 'mvn clean package'
			}
			post {
				success {
					echo 'now archiving'
					archiveArtifacts artifacts: '**/target/*.war'
 					bat 'docker build . -t tomcatwebapp:${env.BUILD_ID}'
				}
			}
		}
		}
}
			
