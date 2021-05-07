pipeline {
	agent any
	
	stages 
	{	
		stage('Build')
		{
			steps
			{
				sh 'npm install'
				sh 'npm build'
			}
		}		
		stage('Test')
		{
			steps
			{
				
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
              			to: 'kamilpodwika123@gmail.com',
              			subject: "Success"
		}			
		failure
		{
			emailext attachLog: true,
                		body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
                		to: 'kamilpodwika123@gmail.com',
                		subject: "Failed"
		}
	}		
}
