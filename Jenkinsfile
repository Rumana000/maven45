   
node('built-in') 
{
    stage('ContinuousDownload') 
    {
       try
       {
         git 'https://github.com/Rumana000/maven45.git'
       }
       catch(Exception e1)
       {
          mail bcc: '', body: 'jenkins is unable to download', cc: '', from: '', replyTo: '', subject: 'download failed', to: 'dev@gmail.com'
          exit(1)
       }   
    }     
    stage('ContinuousBuild') 
    {
       try
       {
          sh 'mvn package'
       }
       catch(Exception e2)
       {
           mail bcc: '', body: 'jenkins is unable to build', cc: '', from: '', replyTo: '', subject: 'build failed', to: 'git@gmail.com'
           exit(1)
       }   
        
    }
    stage('ContinuousDepoyment') 
    {
       try
       {
          
        deploy adapters: [tomcat9(credentialsId: '9f112f2c-a0f0-4415-90cd-63d3b665bd17', path: '', url: 'http://172.31.47.3:8080')], contextPath: 'testapp', war: '**/*.war'
       }
       catch(Exception e3)
       {
          mail bcc: '', body: 'jenkins is unable to deploy', cc: '', from: '', replyTo: '', subject: 'deployment failed', to: 'middleware@gmail.com'
          exit(1)
       }  
       
    }
    stage('ContinuousTesting') 
    {
       try
       {
          git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
          sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
       }
       catch(Exception e4)
       {
          mail bcc: '', body: 'jenkins is unable to download and execute', cc: '', from: '', replyTo: '', subject: 'downloadfailed', to: 'test@gmail.com'
          exit(1)
       }  
    }
    stage('ContinuousDelivery') 
    {
       try
       {
           sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.42.203:/var/lib/tomcat9/webapps/prodapp.war'
       }
       catch(Exception e5)
       {
          mail bcc: '', body: 'jenkins is unable to deliver', cc: '', from: '', replyTo: '', subject: 'delivery failed', to: 'delivery@gmail.com'
       }  
    }      
}    
    
    
    
    

