pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload_loans')
        {
            steps
            {
                git credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', url: 'https://github.com/Gopi806/maven.git'
            }
        }
        stage('ContinuousBuild_loans')
        {
            steps
            {
               sh 'mvn package'
            }
        }
    }
}
