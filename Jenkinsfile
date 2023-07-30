pipeline {
    agent any;
    stages {
        stage("Check files") {
            steps {
                sh "tree -lh"
            }
        }
        stage("Update Certificates from USA-SERVER-1") {
            agent {
                label "usa-server-1"
            }
            steps {
                sh """
                echo $JAVA_HOME
                mvn --version
                """
            }
        }
    }

}