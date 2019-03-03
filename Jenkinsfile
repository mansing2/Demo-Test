pipeline {
	agent { label 'linux' }
	stages {
		stage ('Build') {
			steps {
				echo 'Compiling the code'
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
		stage ('Prod'){
			steps {
				sh "ansible-playbook /home/ubuntu/Ansible_host/ansible-playbook.yml --extra-vars "tag=${env.BUILD_ID}""
			}
		}
		}
}
			
