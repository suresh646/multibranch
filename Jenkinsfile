pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/suresh646/maven.git'   
            }
        }
        stage('Continuousbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Continuousdeploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '39da5159-c3e1-4235-bcd1-af956991575c', path: '', url: 'http://172.31.35.67:8080')], contextPath: 'test', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/suresh646/FunctionalTesting.git'
                
                sh 'java -jar /var/lib/jenkins/workspace/declarative/testing.jar'
            }
        }
        stage('continousDelivery')
        {
            steps
            {
                input message: 'waiting for approval', submitter: 'sureshadmin'
                
                deploy adapters: [tomcat9(credentialsId: '39da5159-c3e1-4235-bcd1-af956991575c', path: '', url: 'http://172.31.35.25:8080')], contextPath: 'prod', war: '**/*.war'
            }
        }
    }
}
