def demo=false
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
	   booleanParam(defaultValue: true, name: 'BusinessService',description: ' ')
	   booleanParam(defaultValue: true, name: 'Notification',description: ' ')
	   booleanParam(defaultValue: true, name: 'ProductService',description: ' ')
	   //booleanParam(defaultValue: true, name: 'QuoteAndOrderWorkflow',description: ' ')
	   
	   choice(name:'Environment',
			  choices:['DEV-MP','DEV-MO','QA','RC','Performance','Prod'],
			  description:'<br/><hr style="border:1px solid green"><strong>Please enter branch name. Default supported branches are (develop,master,release/*)</strong>')
		//string(name: 'ProductService', defaultValue: 'develop',description:'')	  
	    string(name: 'BusinessService', defaultValue: 'develop',description:'')		  
		//string(name: 'Notification', defaultValue: 'develop',description:'')
		//string(name: 'Saltmarsh', defaultValue: 'develop',description:'<hr style="border:1px solid green">')
		//booleanParam(name: 'TriggerAutomation', 
		//			defaultValue: true, 
		//			description:'<span style="color: #FF7433; font-weight: 700; font-size: 1em; padding: 4px 6px; border: 1px solid #008000">No need to change any parameter for automation in case unchecked</span>')
		
		//string(name: 'AutomationBranch', defaultValue: 'develop',description:'')
		//choice(name:'AutomationTestGroup',
		//	  choices:['Sanity','Critical','Full'],
		//	  description:'')
		//choice(name:'BrowserName',
		//	  choices:['Chrome','IE','Firefox'],
		//	  description:'<hr style="border:1px solid green">')	  
	    
		//booleanParam(name: 'TriggerAPIAutomation',defaultValue: true)
		//string(name: 'APIAutomationBranchName', defaultValue: 'develop',description:'')
		//choice(name:'APIAutomationTestGroup',choices:['Smoke','Sanity'],description:'')
		//booleanParam(name: 'RestoreDefaultConfiguration',defaultValue: true)
		booleanParam(defaultValue: true, name: 'DeployQuoteAndOrderWorkflow')
	   
    }
   
  

	agent any

	stages 
	{	stage('Configuring Deployment'){
			steps{
				script{
					businessServiceResourceGroup = getResourceGroupName(params.Environment,'BusinessServices')
					//productServiceResourceGroup = getResourceGroupName(params.Environment,'ProductServices')
					//notificationResourceGroup = getResourceGroupName(params.Environment,'Notification')
					//saltmarshResourceGroup = getResourceGroupName(params.Environment,'Web')
					//testingEnvironment = getAutomationTestingEnvironment(params.Environment)
					deploymentSlot = getDeploymentSlot(params.Environment)
					//deploymentEnvironment = params.Environment
					//automationTriggered = params.TriggerAutomation
					//productUploaderBranch = params.ProductService
				}
			}
		}
		
		stage('deployment')
		{
			parallel{
				stage ('BusinesssService') {
					
					steps
					{
						build job: 'Services/BusinessService',
						parameters: [[$class: 'BooleanParameterValue', name: 'BusinessService', value: params.BusinessService]]
					}
				}
				stage ('Notification') {
					
					steps
					{
						build job: 'Services/Notification',
						parameters: [[$class: 'BooleanParameterValue', name: 'Notification', value: params.Notification]]
					}
				}
				stage ('ProductService') {
					
					steps
					{
						build job: 'Services/ProductService',
						parameters: [[$class: 'BooleanParameterValue', name: 'ProductService', value: params.ProductService]]
					}
				}
				stage ('QuoteAndOrderWorkflow') {
					when{
						expression { params.QuoteAndOrderWorkflow }
					}
					steps
					{
						script{
							demo = params.QuoteAndOrderWorkflow
						}
						build job: 'Services/QuoteAndOrderWorkFlow',
						//parameters:   [[$class: 'BooleanParameterValue', name: 'LogicApp', value: params.LogicApp]]
						parameters: [[$class: 'StringParameterValue', name: 'TargetResourceGroup', value: businessServiceResourceGroup],
										[$class: 'StringParameterValue', name: 'SourceBranch', value: params.BusinessService],
										[$class: 'StringParameterValue', name: 'TargetSlot', value: deploymentSlot ]]	
					}
				}
			}
		}
	}
}

stage ('QuoteAndOrderWorkflow') {
	if(demo)
	{
		build job: 'Services/QuoteAndOrderWorkFlow',
		//parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp3Click', value: params.LogicApp3click],
		//parameters:  [[$class: 'BooleanParameterValue', name: 'LogicApp', value: params.LogicApp]]
			parameters: [[$class: 'StringParameterValue', name: 'TargetResourceGroup', value: businessServiceResourceGroup],
										[$class: 'StringParameterValue', name: 'SourceBranch', value: params.BusinessService],
										[$class: 'StringParameterValue', name: 'TargetSlot', value: "production" ]]
	}
}
