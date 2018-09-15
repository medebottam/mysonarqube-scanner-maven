pipeline {
    agent any
    tools {
        maven 'M3'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M3 = ${M3}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn clean install sonar:sonar' 
            }
        }
        stage('SonarQube analysis') { 
         steps { 
          sh '/opt/sonar-scanner-3.2.0.1227-linux/bin/sonar-scanner -Dproject.settings=./sonar-project.properties' 
        }
    }
    }
}
