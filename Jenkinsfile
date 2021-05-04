pipeline {
	agent any
	
	stages 
	{				
		stage('Test')
		{
			steps
			{
				sh 'npm install'
				sh 'npm test'
				echo 'Test'
			}
		}
	}		
	post
	{
		success
		{
			emailext attachLog: true,
                		body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
              			recipientProviders: [developers(), requestor()],
              			to: 'kamilpodwika@interia.pl',
              			subject: "Success"
		}			
		failure
		{
			emailext attachLog: true,
                		body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
                		recipientProviders: [developers(), requestor()],
                		to: 'kamilpodwika@interia.pl',
                		subject: "Failed"
		}
	}		
}
