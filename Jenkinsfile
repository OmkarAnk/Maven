node('built-in') 
{
    stage('Continuous download') 
    {
        try
        {
	    git 'https://github.com/OmkarAnk/maven.git'
	}
        catch (Exception e1)
        {
            mail bcc: '', body: 'Jenkins unable to download the code', cc: '', from: '', replyTo: '', subject: 'Continuous download failed', to: 'gitadmin@gmail.com'
            exit(1)
        }
    }
    stage('Continuous build') 
    {
        try
        {
            sh 'mvn package'
        }   
        catch (Exception e2)
        {
            mail bcc: '', body: 'Jenkins is unable to build the code', cc: '', from: '', replyTo: '', subject: 'Continuous download failed', to: 'gitadmin@gmail.com'
            exit(1)
        }
    }
    stage('Continuous deploy') 
    {
        try
        {
            sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/trial3/webapp/target/webapp.war ubuntu@172.31.5.154:/var/lib/tomcat9/webapps/testapp.war'
        }   
        catch (Exception e3)
        {
            mail bcc: '', body: 'Jenkins s deploy to the artifact', cc: '', from: '', replyTo: '', subject: 'Continuous deployment failed', to: 'gitadmin@gmail.com'
            exit(1)
        }
    }
    stage('Continuous test') 
    {
        try
        {
          git 'https://github.com/OmkarAnk/Functional_testing.git'
          sh 'java -jar /home/ubuntu/.jenkins/workspace/trial3/testing.jar'
        }   
        catch (Exception e4)
        {
            mail bcc: '', body: 'testing failed', cc: '', from: '', replyTo: '', subject: 'Continuous testing failed', to: 'gitadmin@gmail.com'
            exit(1)
        }
    }
    stage('Continuous delivery') 
    {
        try
        {
          sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/trial3/webapp/target/webapp.war ubuntu@172.31.10.75:/var/lib/tomcat9/webapps/prodapp.war'
        }   
        catch (Exception e5)
        {
            mail bcc: '', body: 'continuous delivery failed', cc: '', from: '', replyTo: '', subject: 'Continuous testing failed', to: 'gitadmin@gmail.com'
            exit(1)
        }
    }
}
