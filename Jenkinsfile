pipeline {
    agent any

    tools {
        jdk 'jdk1.8'
        maven 'maven3.3'
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
                    sh 'echo "${WORKSPACE}" '
                    war_name='test-jenkinsfile_master'
                    host ='172.16.0.217'
                    user = 'root'
                    passwd ='yst9ol.0p;/'
                        sh """
                            cd ${WORKSPACE}/target
                            /usr/bin/sshpass -p'$passwd' scp -o StrictHostKeyChecking=no *.jar '$user'@'$host':/opt/testp/
                        """
                }
            }
        }
    }
}