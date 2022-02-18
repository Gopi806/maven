pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', url: 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
               sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', path: '', url: 'http://172.31.3.201:8080')], contextPath: 'test2', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', url: 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContinousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', path: '', url: 'http://172.31.2.229:8080')], contextPath: 'prod2', war: '**/*.war'
            }
        }
        
    }
}
