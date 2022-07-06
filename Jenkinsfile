pipeline
{
	agent any
	stages {
		stage('Pull') {
				steps{
					script{
						checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[ credentialsId: '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', url: 'https://github.com/tchapa1/continuedDelivery.git']]])
						}
					}
				}
				
				
				
		stage('Build') {
				steps{
          				script{
						sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
						}
					}
				}


		}
}				
				
				
