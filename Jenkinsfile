pipeline {
    agent any
      environment {
        DATE = new Date().format('yy.M')
        TAG = "${DATE}.${BUILD_NUMBER}"
    }
    stages{
        stage('compile') {
            steps {
                sh 'mvn validate compile'
            }
        }
        stage('unit-testing') {
            steps {
                sh 'mvn test'
            }
        }
        stage('sonar-analysis') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.host.url=http://35.177.21.220:9000 -Dsonar.login=1a4202d3c5cb019cd2b66ae21a9d9e784075073d'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('publish-artifacts') {
            steps {
                sh 'mvn deploy'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.build("deepika2chebolu/aws-rds:${TAG}")
                }
            }
        }
        stage('Pushing Docker Image to Dockerhub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com','docker_credential') {
                        docker.image("deepika2chebolu/aws-rds:${TAG}").push()
                        docker.image("deepika2chebolu/aws-rds:${TAG}").push("latest")
                    }
                }
            }
        }
        stage('deploy') {
            steps {
                node('n1') {
                    sh 'docker stop aws-rds |true'
                    sh 'docker rm aws-rds | true'
                    sh 'docker container run -dt -p 9091:8080 deepika2chebolu/aws-rds:${TAG}'
                }
            }
        }
    }
}    
