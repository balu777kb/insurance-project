pipeline {
    agent any 
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/balu777kb/insurance-project.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Build docker image') {
            steps {  
                sh 'docker build -t insure .'
                sh 'docker tag insure:latest balu777kb/insurance:latest'
            }
        }
        
     }
}
