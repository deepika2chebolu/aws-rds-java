pipeline {
    agent any
      environment {
        registry = "072669763386.dkr.ecr.eu-west-2.amazonaws.com/my-repo"
    }
    stages{
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/deepika2chebolu/aws-rds-java.git']]])
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        stage('Docker push') {
            steps {
                script {
                    sh 'aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin 072669763386.dkr.ecr.region.amazonaws.com'
                    sh 'docker push 072669763386.dkr.ecr.region.amazonaws.com/my-repository:latest'
                 }
            }
        }
    }
}    
