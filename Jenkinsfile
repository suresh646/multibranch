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
    }
}
