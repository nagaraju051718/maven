pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
         stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '625810e3-8b6a-4803-a9dd-10a5f1ba203e', path: '', url: 'http://172.31.30.182:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
               sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '625810e3-8b6a-4803-a9dd-10a5f1ba203e', path: '', url: 'http://172.31.28.111:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}
