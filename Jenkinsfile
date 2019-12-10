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
	   booleanParam(defaultValue: true, name: 'QuoteAndOrderWorkflow',description: ' ')
	   
    }
   
  

	agent any

	stages 
	{	
		
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
						parameters:   [[$class: 'BooleanParameterValue', name: 'LogicApp', value: params.LogicApp]]

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
		parameters:  [[$class: 'BooleanParameterValue', name: 'LogicApp', value: params.LogicApp]]
	}
}
