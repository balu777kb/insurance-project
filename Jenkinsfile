pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker')
    }
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
                sh 'docker tag insure:latest balu777kb/insurance12:latest'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push balu777kb/insurance12:latest'
               }
          }
   
        stage('Deploy') {
             steps{
                   sh 'docker run -itd --name insuranceproject46 -p 8096:8096 balu777kb/insurance12:latest'
             }
        }   
}
       post {
            always {
               sh 'docker logout'   
            }
    }
}
