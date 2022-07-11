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
          				        sh "npm install"
						sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
						}
					}
				}
							
				
				
		stage('Docker') {
				steps {
					script{
						sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
						}
					}
				}
				
						
		stage('Docker-registry') {
				steps {
					script{
						sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml"
						}
					}
				}
				
								
		stage('Mail de confirmation') {
            			steps {
               				emailext attachLog: true, body: 'la tache a ete terminée avec succées', subject: 'Confirmation de Jenkins', to: 'esprit.devops@gmail.com'
            				}
            					}

                
                stage('Fin') {
                		steps { echo "Ok"}
                		}



		}
		
    post{
        failure{
            mail to: "esprit.devops@gmail.com",
            subject: "Project CD Terminé avec un probleme ",
            body: "***************Bonjour************** Verifiez votre Pipeline PIPE1 ,vous avez un probleme "
                }
        }
}				
				
				
