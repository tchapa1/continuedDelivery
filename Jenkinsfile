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
				
				
