pipeline
{
	agent any
    stages
    {
        
       
        /*stage ("syntax error check")
        {
            steps
            {
                echo "This is Demo"
            }
        }*/
	 
	stage ("Get Source") 
	{
        // run a command to get the source code download
		steps {
        	magento21.inside('-v /home/git/repos:/home/git/repos') 
		{
            		//sh "rm -rf gradle-greetings"
			sh "git clone https://github.com/ChandradeepKumar/magento21.git"
		}}
    	}    
	    
	 /*stage ("unit test")
	    {
		    steps
		    {
			    sh 'chmod 0775 vendor/bin/phpunit '
			    sh 'vendor/bin/phpunit -c dev/tests/unit/phpunit.xml.dist app/code/Nagarro/Designashade/Test/Unit/Model/DesignashadefacadeTest.php '
		    }
	    }
	stage ("sonar")
        {
            steps
            {
                sh '/opt/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner -Dsonar.projectKey="abc1" -Dsonar.projectname=serena1 -Dsonar.sources=.'
                //sh '/opt/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner'
            }
        } 
	
	    stage ("Image Build")
	    {
	        steps
	        {
		          sh 'docker build -t magento_21 .' //build image
	        }
	    }
  
  
	    stage('Image Run')
      {
          steps
          {
            sh 'docker rm -f cont1'
            sh 'docker run --name cont1 -i -d -p 9096:80 magento_21 '
          }
      }*/
  }  

    
}
