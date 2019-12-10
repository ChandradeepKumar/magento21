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
	   booleanParam(defaultValue: true, name: 'LogicApp1click',description: ' ')
	   booleanParam(defaultValue: true, name: 'LogicApp2click',description: ' ')
	   booleanParam(defaultValue: true, name: 'LogicApp3click',description: ' ')
	   booleanParam(defaultValue: true, name: 'LogicApp4click',description: ' ')
	   
    }
   
  

	agent any

	stages 
	{
		stage('deployment')
		{
			parallel{
				stage ('BusinesssService') {
					when{
						expression { params.LogicApp1click }
					}
					steps
					{
						build job: 'Services/BusinessService',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp1Click', value: params.LogicApp1Click]]
					}
				}
				stage ('Notification') {
					when{
						expression { params.LogicApp2click }
					}
					steps
					{
						build job: 'Services/Notification',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp2Click', value: params.LogicApp1Click]]
					}
				}
				stage ('ProductService') {
					when{
						expression { params.LogicApp3click }
					}
					steps
					{
						build job: 'Services/ProductService',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp3Click', value: params.LogicApp3Click]]
					}
				}
				stage ('QuoteAndOrderWorkflow') {
					when{
						expression { params.LogicApp4click }
					}
					steps
					{
						script{
							demo = params.LogicApp4click
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
