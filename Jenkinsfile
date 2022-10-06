pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                git 'https://github.com/deepika2chebolu/aws-rds-java.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy') {
            steps {
                sshagent(credentials:['n1']) {
                    sh 'ssh -T -o StrictHostKeyChecking=no centos@172.31.86.65'
                sh 'scp -r /var/lib/jenkins/workspace/PROJECT/target/*.war centos@172.31.86.65:/home/centos/apache-tomcat-7.0.94/webapps'
                }
            }
        }
    }
}    
