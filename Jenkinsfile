pipeline {
	agent { label 'linux' }
	stages {
		stage ('Build') {
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
		stage ('Pre-Prod'){
			steps {
				sh "docker run -dit -p 8888:8080 tomcatwebapp:${env.BUILD_ID}"
			}
		}
		}
}
			
