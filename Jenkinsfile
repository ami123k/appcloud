 pipeline {
  agent any
    stages {
	stage('terraform') {
				steps {
					script{
						sh "terraform init /root/monprojet/main.tf" 
					}
				}
			} 
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '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',
                            url: 'https://github.com/ami123k/appcloud.git']]])
                }
            }
        }
    stage('Build') {
				steps {
					script{
						sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml " 
					}
				}
			} 
    stage('docker') {
				steps {
					script{
						sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml " 
					}
				}
			}  
   	    
	 
  stage('docker-registry') {
				steps {
					script{
						sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml " 
					}
				}
			}   
 }
}

