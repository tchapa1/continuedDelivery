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
							
				
				
		stage('docker') {
				steps {
					script{
						sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
						}
					}
				}
				
						
		stage('docker-registry') {
				steps {
					script{
						sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml"
						}
					}
				}
				
								
		stage('Mail de confirmation') {
                		steps { emailext(attachLog: true, body: 'ci-joint le rapport de votre Pipeline', subject: 'Rapport Pipeline devops Esprit', to: 'hamza.smari@esprit.tn')}                
                				}

                
                stage('Fin') {
                		steps { echo "Ok"}
                		}



		}
		
    post{
        always{
            mail to: "esprit.devops@gmail.com",
            subject: "Project CD Terminé avec succés",
            body: "***************Bonjour**************
            La tache d'aujourd'hui a été terminée avec succés
            Merci"
                }
        }
}				
				
				
