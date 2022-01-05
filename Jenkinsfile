pipeline {
    agent any

    stages {
            stage('compile') {
                steps {
		            script{
                    dir('/Users/jorgeignacioramireevans/Devops/ejemplo-maven'){
                    sh'./mvnw clean test -e'
                    }
                }
            }
           }

          stage('test') {
                steps {
		            script{
                    dir('/Users/jorgeignacioramireevans/Devops/ejemplo-maven'){
                    sh'./mvnw clean test -e'
                    }
                }
            }
           }
        stage('jar') {
                steps {
		            script{
                    dir('/Users/jorgeignacioramireevans/Devops/ejemplo-maven'){
                    sh'./mvnw clean package -e'
                    }
                }
            }
           }
         stage('run') {
                steps {
		            script{
                        dir('/Users/jorgeignacioramireevans/Devops/ejemplo-maven'){
                    sh'nohup bash mvnw spring-boot:run &'
                    sleep 20 
                }
                }
            }
           }
        stage('testing') {
                steps {
		            script{
                    sh "curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'"
                }
            }
           }
    }
}


