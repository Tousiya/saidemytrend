pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
     }

     stages {

         stage('Build') {
             steps {
                 sh 'mvn clean deploy'
             }
         }

         stage('SonarQube analysis') {
             environment {
                 scannerHome = tool 'Sonar-cred'
           
             }

             steps {
                withSonarQubeEnv('SonarQube-Server') {

                    sh "${scannerHome}/bin/sonar.scanner"

                }

             }

         }

      }

}
