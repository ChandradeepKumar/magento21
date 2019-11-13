pipeline
{
	agent any

	stages
	{
		stage ('Invoke_pipelineA') {
			steps {
				script
				{
					if(CheckIn == "yes")
					{
						echo "Checkbox is checked !!!!"
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
