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
				
				
