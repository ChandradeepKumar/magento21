def demo;
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
		stage('deployment')
		{
			parallel{
				stage ('deploy1') {
					when{
						expression { params.LogicApp1click }
					}
					steps
					{
						build job: 'test 123 456 abc',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp1Click', value: params.LogicApp1Click]]
					}
				}
				stage ('deploy2') {
					when{
						expression { params.LogicApp1click }
					}
					steps
					{
						build job: 'test 123 456 abc',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp1Click', value: params.LogicApp1Click]]
					}
				}
				stage ('deploy3') {
					when{
						expression { params.LogicApp1click }
					}
					steps
					{
						script{
							demo = params.LogicApp1click
						}
						build job: 'test 123 456 abc',
						parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp1Click', value: params.LogicApp1Click]]
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
		parameters: [[$class: 'BooleanParameterValue', name: 'LogicApp1Click', value: params.LogicApp1Click]]
	}
}
