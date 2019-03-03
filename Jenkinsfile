pipeline {
	agent { label 'linux' }
	stages {
		stage ('build') {
			steps {
				sh 'mvn clean package'
			}
			post {
				success {
					echo 'Building Dockerfile'
					sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
				}
			}
		}
		}
}
			
