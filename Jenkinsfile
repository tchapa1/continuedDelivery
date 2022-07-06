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


		}
}				
				
				
