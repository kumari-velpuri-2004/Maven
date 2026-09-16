pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'c6ec7649-5a47-44a3-bb07-a1c52b3f103c', path: '', url: 'http://172.31.12.37:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'c6ec7649-5a47-44a3-bb07-a1c52b3f103c', path: '', url: 'http://172.31.5.132:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
