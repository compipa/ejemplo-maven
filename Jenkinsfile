pipeline {
    agent any

    stages {
            stage('compile') {
                steps {
		            script{
                    bat'./mvnw.cmd clean compile -e'
                }
            }
           }

          stage('test') {
                steps {
		            script{
                    bat'./mvnw.cmd clean test -e'
                }
            }
           }
        stage('jar') {
                steps {
		            script{
                    bat'./mvnw.cmd clean package -e'
                }
            }
           }
         stage('run') {
                steps {
		            script{
                    bat'start /min mvnw.cmd spring-boot:run &'
                    sleep 20 
                }
            }
           }
    }
}

