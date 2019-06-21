#!groovy
import hudson.model.*
import hudson.EnvVars
import groovy.json.*
import java.net.URL 

def test()
{
	echo "demo";
}

node('slave_node')
{
    //agent any
    //stages
    //{
        stage ("syntax error check")
	test()
	 
	/*stage ("sonar")
        {
            steps
            {
                //sh 'sonar-scanner -Dsonar.projectKey="abc" -Dsonar.sources=.'
                sh '/opt/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner'
            }
        } */
	
	    /*stage ("Image Build")
	    {
	        steps
	        {
		          sh 'docker build -t magento_21 .' //build image
	        }
	    }*/
  
  
	    /*stage('Image Run')
      {
          steps
          {
            sh 'docker rm -f cont1'
            sh 'docker run --name cont1 -i -d -p 9096:80 magento_21 '
          }
      }*/
  //}  

    
}
