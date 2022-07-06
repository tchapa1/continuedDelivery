pipeline
{
	agent any
	stages {
		stage('Pull') {
				steps{
					script{
						checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[ credentialsId: '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', url: 'https://github.com/tchapa1/continuedDelivery.git']]])
						}
					}
				}


		}
}				
				
				
