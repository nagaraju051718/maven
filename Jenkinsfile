	pipeline
{
    agent any 
    stages
    {
        stage('continuousDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '01471035-fabd-4831-bf1b-13f4ef7a2657', path: '', url: 'http://172.31.23.193:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('continuousTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar testing.jar'
            }
        }
        stage('continuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '748403f5-5cce-4b12-9616-e06056a5e050', path: '', url: 'http://172.31.29.8:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
