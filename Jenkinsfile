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
                    docker.withRegistry('https://072669763386.dkr.ecr.eu-west-2.amazonaws.com', 'ecr:eu-west-2:ecr_credential') {
                        docker.image('demo').push('latest')
                    }
                 }
            }
        }
    }
}    
