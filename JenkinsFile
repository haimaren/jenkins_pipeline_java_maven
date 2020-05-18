pipeline {
    agent any

    tools {
        jdk 'jdk1.8'
        maven 'mvn3.3'
    }

    stages {
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage ('Publish to Test-D') {
            steps {
                script {
                    def remote = [:]
                    remote.name = 'dev-tst'
                    remote.host ='172.16.0.217'
                    remote.user = 'root'
                    remote.password ='yst9ol.0p;/'
                    remote.allowAnyHosts= true
                    sshPut remote: remote, from: '*/target/*.jar', into: '/opt/testp/'
                }
            }
        }
    }
}