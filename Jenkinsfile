pipeline
{
		
   parameters {
        //string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        //text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        //booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(bydefaultValue: 'yes' name: 'Magento',choices: ['yes','No'], description: 'Pick something')
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
}
