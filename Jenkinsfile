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
                keytool -delete -noprompt -alias app-nx -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit
                keytool -import -alias app-nx -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit -file ${env.WORKSPACE}/app-nx/certificate.crt
                """
            }
        }
    }

}