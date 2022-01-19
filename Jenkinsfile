pipeline {
    agent any

    stages {
        stage('Donwload-Nexus') {
            steps {
                script {
						bat "curl -X GET -u admin:Dominga.2404 http://527f-190-95-121-196.ngrok.io/repository/test-repo/com/devopsusach2020/DevOpsUsach2020/0.0.1/DevOpsUsach2020-0.0.1.jar -O"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    bat "mvn clean test -e"
                }
            }
        }
	
        stage('Package') {
            steps {
                script {
                    bat "mvn clean package -e"
                }
            }
        }
        stage('Run') {
            steps {
                script {
                    bat "start /min mvn spring-boot:run &"
                }
            }
        }

        stage('Upload to Nexus') {
             steps {
                 bat 'echo ${WORKSPACE}'
                 script {
                     nexusPublisher nexusInstanceId: 'nexus_local', nexusRepositoryId: 'taller10', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: "${WORKSPACE}/DevOpsUsach2020-0.0.1.jar"]], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '1.0.0']]]
                 }
             }
         }
         
        stage('Test Applications') {
            steps {
                script {
                    bat "start chrome http://localhost:8081/rest/mscovid/test?msg=testing"
					
                }
            }
        }
    }
}