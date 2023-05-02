node('built-in')
{
    stage('continuousdownload') 
    {
       git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuousbuild') 
    {
       sh 'mvn package'
    }
    stage('continuousdeployment') 
    {
       deploy adapters: [tomcat9(credentialsId: '17c8f4f7-5b9e-4f61-ad74-d93bc2d0280b', path: '', url: 'http://172.31.7.120:8080')], contextPath: 'testapp', war: '**/*.war' 
    }
    stage('continuoustesting') 
    {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    stage('continuousdelivery') 
    {
       deploy adapters: [tomcat9(credentialsId: '17c8f4f7-5b9e-4f61-ad74-d93bc2d0280b', path: '', url: 'http://172.31.4.16:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
  
  
  
}


