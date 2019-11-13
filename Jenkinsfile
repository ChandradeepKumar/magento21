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
