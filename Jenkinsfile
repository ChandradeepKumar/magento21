pipeline
{
	agent any
	
    stages
    {
        
       
        stage ("syntax error check")
        {
            steps
            {
                echo "This is Demo"
            }
        }
	
	/*stage ("Get Source") 
	{
        // run a command to get the source code download
		
		
			
			steps 
			{
				script
				{
				myImg = docker.image("ubuntu:latest")
				myImg.pull()
        			myImg.inside('-v /home/git/repos:/home/git/repos') 
				{
            		//sh "rm -rf gradle-greetings"
					//sh 'apt-get -y install git'
				 //sh "git clone https://github.com/ChandradeepKumar/magento21.git"
					sh ' /opt/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner -h'
					echo "inside method is working fine"
				}
				}
			}
		
    	}    */
    	
	    
	/*stage ("sonar") 
	{
        // run a command to get the source code download
		
		
			
			steps 
			{
				script
				{
				myImage = docker.image("ubuntu1:latest")
				myImage.pull()
        			myImage.inside('-v /home/git/repos:/home/git/repos') 
				{
            		//sh "rm -rf gradle-greetings"
					//sh 'apt-get -y install git'
				 //sh "git clone https://github.com/ChandradeepKumar/magento21.git"
					sh '/sonar-scanner-4.0.0.1744-linux/bin/sonar-scanner -h'

					sh 'php -v'
					echo "inside method is working fine"
				}
				}
			}
		
    	}    */
	    
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
                sh '/opt/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner -h'
                //sh '/opt/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner'
            }
        } 
	*/
	    stage('Setup') {
            steps {
                script {
                    startZap(host: "127.0.0.1", port: 8090, timeout:500, zapHome: "/ZAP_2.8.0", allowedHosts:['10.175.16.205']) // Start ZAP at /opt/zaproxy/zap.sh, allowing scans on github.com (if allowedHosts is not provided, any local addresses will be used 
			runZapCrawler(host: "https://localhost")
			runZapAttack(userId: 5, scanPolicyName: "yourScanPolicy")
                }
            }
        }
	    
	    
	    /*stage ("Image Build")
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
