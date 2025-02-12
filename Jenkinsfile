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
                 scannerHome = tool 'SonarQube-cred'
           
             }

             steps {
                withSonarQubeEnv('SonarQube-Scanner') {

                    sh "${scannerHome}/bin/sonar.scanner"

                }

             }

         }

      }

}
