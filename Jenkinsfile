pipeline
{
		
   parameters {
        //string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        //text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        //booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        //choice(name: 'Magento',choices: ['yes','No'], description: 'Pick something')
	//extendedChoice(ParameterType:'checkbox' name: 'test123',description: 'pick up')

       // password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
       booleanParam(name: 'CheckIn',defaultValue: true) 
    }
   
  

	agent any

	stages
	{
		stage ('Invoke_pipelineA') {
			steps {
				script
				{
					if(CheckIn == "yes")
					{
						build job: 'Magento'
					}
					else
					{
						echo "Not Checked !!!"
					}
				}
			}
		}
	}
}
