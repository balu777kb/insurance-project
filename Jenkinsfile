pipeline {
    agent any 
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/balu777kb/health-care.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
    }
}
