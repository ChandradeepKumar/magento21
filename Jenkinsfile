pipeline
{
		
   parameters {
        //string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        //text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        //booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'Magento',choices: ['yes','No','do','123'], description: 'Pick something')
	//extendedChoice(ParameterType:'checkbox' name: 'test123',description: 'pick up')

       // password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
       
	   //booleanParam(defaultValue: true, name: 'CheckIn',description: ' ')
	   booleanParam(defaultValue: true, name: 'LogicApp1click',description: ' ')
    }
   
  

	agent any

	stages
	{
		stage ('deploy') {
			steps
			{
				build job: 'test 123 456 abc',
				parameters: [[$class: 'BooleanParameterValue', name: 'CheckIn', value: params.CheckIn]]
			}
		}
		
		
		/*stage ('deploy') {
			steps
			{
				sh 'echo "it is working fine"'
			}
		}*/
		/*stage ('Invoke_pipelineB') {
			steps {
				script
				{
					if(Check == "true")
					{
						build job: 'Magento'
						//build job: 'serena_ci/master'
					}
					else
					{
						echo "Not Checked !!!"
					}
				}
			}
		}*/
	}
	post 
    {
        success 
        {      
            //mail to: "chandradeep.kumar@nagarro.com", //TODO: pick emails from configuration
            //subject: "Build Success: ${currentBuild.fullDisplayName}", 
            //body: "View build report here: ${env.BUILD_URL}",
            
          emailext // attachmentsPattern :"serenaTest/linux/SM_AUTOMATION/TestReports/Report/extentreport.html, serenaTest/linux/SerenaPro_AUTOMATION/TestReports/Report/extentreport.html",
            body: """View build report here: ${env.BUILD_URL}
		<TABLE>
		  <TR>
			if(LogicApp1Deploy == "true")
			{
				<TD> service is : </TD>
				<TD> $LogicAppDeploy </td>
			}
		  </TR>
		  
		</TABLE>""",
		
            subject: "Build Success: ${currentBuild.fullDisplayName}", 
            mimeType: 'text/html', 
            to: 'chandradeep.kumar@nagarro.com'
        }
                
        failure
        {
            //mail to: "chandradeep.kumar@nagarro.com", //TODO: pick emails from configuration
            //subject: "Build Failure: ${currentBuild.fullDisplayName}",
            //body: "View build report here: ${env.BUILD_URL}" 
            //emailext body: "failure: ${env.BUILD_URL}" , subject: 'Build Failure', to: 'vineet.sajwan@nagarro.com,chandradeep.kumar@nagarro.com'
          //emailext  attachmentsPattern :"serenaTest/linux/SM_AUTOMATION/TestReports/Report/extentreport.html",body: "successful: ${env.BUILD_URL}", subject: 'Testing', mimeType: 'text/html', to: 'chandradeep.kumar@nagarro.com'
          
          emailext  //attachmentsPattern :"serenaTest/linux/SM_AUTOMATION/TestReports/Report/extentreport.html, serenaTest/linux/SerenaPro_AUTOMATION/TestReports/Report/extentreport.html",
            body: "View build report here: ${env.BUILD_URL}", 
            subject: "Build FAILURE: ${currentBuild.fullDisplayName}", 
            mimeType: 'text/html', 
            to: 'chandradeep.kumar@nagarro.com'
        }
    }
	
}
