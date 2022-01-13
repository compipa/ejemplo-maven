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
           stage('sonar') {
                steps {
		            script{
                    dir('/Users/jorgeignacioramireevans/Devops/ejemplo-maven'){
                    sh'mvn clean verify sonar:sonar \
                      -Dsonar.projectKey=ejemplo-maven \
                      -Dsonar.host.url=http://localhost:9000 \
                      -Dsonar.login=9dab1a1d6328408762c2c87bf85cee8064f9aafd'
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


