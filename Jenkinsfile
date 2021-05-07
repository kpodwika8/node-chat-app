pipeline {
	agent any
	
	tools{nodejs "nodejs"}
	
	stages 
	{	
		stage('Build')
		{
			steps
			{	
				echo 'Building'
				sh 'npma install'
			}
			post
			{
				always
				{
					echo 'Zakonczono budowanie'
				}
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
		stage('Test')
		{
			steps
			{				
				sh 'npm test'
				echo 'Test'			
			}
		
			
			post
			{
				always
				{
					echo 'Zakonczono testowanie'
				}
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
	}		
}
