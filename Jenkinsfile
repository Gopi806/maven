pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload_master')
        {
            steps
            {
                git credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', url: 'https://github.com/Gopi806/maven.git'
            }
        }
        stage('ContinuousBuild_master')
        {
            steps
            {
               sh 'mvn package'
            }
        }
        stage('ContinuousDeployment_master')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', path: '', url: 'http://172.31.3.201:8080')], contextPath: 'test2', war: '**/*.war'
            }
        }
        stage('ContinuousTesting_master')
        {
            steps
            {
                git credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', url: 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContinousDelivery_master')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '93c02cb2-03f4-4be0-bb78-57e3403d891a', path: '', url: 'http://172.31.2.229:8080')], contextPath: 'prod2', war: '**/*.war'
            }
        }
        
    }
}
