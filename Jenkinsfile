pipeline
{
    agent any 
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/kumari-velpuri-2004/Maven.git'
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
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.22.88:/var/lib/tomcat10/testapp.war'
            }
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/kumari-velpuri-2004/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'

            }
        }
        stage('Delivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.26.195:/var/lib/tomcat10/prodapp.war'
            }
        }
    }
}
