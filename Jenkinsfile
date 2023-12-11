   
node('built-in') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/Rumana000/maven45.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDepoyment') 
    {
        deploy adapters: [tomcat9(credentialsId: '9f112f2c-a0f0-4415-90cd-63d3b665bd17', path: '', url: 'http://172.31.47.3:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh '''java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar
'''
    }
    stage('ContinuousDelivery') 
    {
        deploy adapters: [tomcat9(credentialsId: '9f112f2c-a0f0-4415-90cd-63d3b665bd17', path: '', url: 'http://172.31.42.203:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}    
    
    
    
    

