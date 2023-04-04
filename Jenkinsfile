node('built-in') 
{
    stage('Download_feature') 
    {
        try
        {
	    git 'https://github.com/OmkarAnk/maven.git'
        }   
        catch (Exception e1)
        {
            mail bcc: '', body: 'Jenkiins unable to download the code', cc: '', from: '', replyTo: '', subject: 'Continuous download failed', to: 'gitadmin@gmail.com'
            exit(1)
        }
    }
    stage('Build_feature') 
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

 }
