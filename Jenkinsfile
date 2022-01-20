pipeline {
    agent any

    stages {
        stage('Donwload-Nexus') {
            steps {
                script {
						bat "curl -X GET -u admin:Dominga.2404 http://c010-190-95-121-196.ngrok.io/repository/test-repo/com/devopsusach2020/DevOpsUsach2020/0.0.1/DevOpsUsach2020-0.0.1.jar -O"
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

                stage('Test') {
            steps {
                script {
                    bat "mvn clean test -e"
                }
            }
        }

        stage('Upload to Nexus') {
             steps {
                 bat 'echo ${WORKSPACE}'
                 script {
                    nexusPublisher nexusInstanceId: 'Nexus-test', nexusRepositoryId: 'test-repo', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'DevOpsUsach2020-0.0.1']], mavenCoordinate: [artifactId: 'DevOpsUsach20200', groupId: 'com.devopsusach2020', packaging: 'jar', version: '1.0.0']]]
                 }
             }
         }


    }
}