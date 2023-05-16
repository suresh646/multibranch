node
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/sureshnemala/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeploy')
    {
        deploy adapters: [tomcat9(credentialsId: '3d998c6a-a626-457b-95ff-87ffe25022bb', path: '', url: 'http://172.31.29.233:8080')], contextPath: 'test', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/sureshnemala/FunctionalTesting.git'
        
        sh 'java -jar /var/lib/jenkins/workspace/scripted/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '3d998c6a-a626-457b-95ff-87ffe25022bb', path: '', url: 'http://172.31.20.131:8080')], contextPath: 'prod', war: '**/*.war'
    }
}
