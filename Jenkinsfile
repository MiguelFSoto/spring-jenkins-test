pipeline {
    agent any
  
    stages {
        stage('Build') {
            steps {
                // To run Maven on a Windows agent, use
                // 
                sh "./mvnw -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    //junit '**/target/surefire-reports/TEST-*.xml'
                    dir("./target")
                        sh 'java -jar spring-petclinic-3.1.0-SNAPSHOT.jar'
                    }
                }
            }
        }
    }
}
