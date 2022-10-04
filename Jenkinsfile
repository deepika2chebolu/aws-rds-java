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
                    sh 'ssh -T -o StrictHostKeyChecking=no centos@54.237.84.250'
                sh 'scp -r /var/lib/jenkins/workspace/PROJECT/target/*.war centos@54.237.84.250:/home/centos/apache-tomcat-7.0.94/webapps'
                }
            }
        }
    }
}    
