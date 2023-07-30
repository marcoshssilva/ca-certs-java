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
                keytool -importcert -noprompt -alias app-nx -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit -file "./app-nx/certificate.crt"
                """
            }
        }
        stage("Update Certificates from BR-SERVER-1") {
            agent {
                label "br-server-4"
            }
            steps {
                sh """
                keytool -importcert -noprompt -alias app-nx -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit -file "./app-nx/certificate.crt"
                """
            }
        }
    }

}
