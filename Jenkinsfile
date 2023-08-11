pipeline {
    agent any

    //tools {
        // Install the Maven version configured as "M3" and add it to the path.
        //maven "M3"
    //}

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                //powershell 'git clone https://github.com/MiguelFSoto/spring-jenkins-test.git'
                //git 'https://github.com/MiguelFSoto/spring-jenkins-test.git'
                
                // Run Maven on a Unix agent.
                // sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // 
                bat "mvnw.cmd -Dmaven.test.failure.ignore=true clean package"
                //bat "mvnw.cmd -Dmaven.test.failure.ignore=true clean"
                //bat "mvnw.cmd -Dmaven.test.failure.ignore=true compile"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    //junit '**/target/surefire-reports/TEST-*.xml'
                    powershell "pwd"
        
                    dir("./target")
                    {
                        echo "develop server"
                        powershell 'java -jar spring-petclinic-3.1.0-SNAPSHOT.jar'
                    }
                }
            }
        }
    }
}
