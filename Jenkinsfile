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
	   
    }
   
  

	agent any

	stages 
	{
		stage('deployment')
		{
			parallel{
				stage ('deploy1') {
					when{
						expression { params.LogicApp1click }
					}
					steps
					{
						build job: '1-click-deployment',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp1Click', value: params.LogicApp1Click]]
					}
				}
				stage ('deploy2') {
					when{
						expression { params.LogicApp2click }
					}
					steps
					{
						build job: '1-click-QA-RC',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp2Click', value: params.LogicApp1Click]]
					}
				}
				stage ('deploy3') {
					when{
						expression { params.LogicApp3click }
					}
					steps
					{
						script{
							demo = params.LogicApp3click
						}
						build job: 'test 123 456 abc',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp3Click', value: params.LogicApp3Click],
						parameters:   [$class: 'BooleanParameterValue', name: 'LogicApp', value: params.LogicApp]]

					}
				}
			}
		}
	}
}

stage ('deploy production') {
	if(demo)
	{
		build job: 'test 123 456 abc',
		parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp3Click', value: params.LogicApp3Click],
		parameters:  [$class: 'BooleanParameterValue', name: 'LogicApp', value: params.LogicApp]]
	}
}
