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
          sh 'mvn clean install sonar:sonar ' + 
          '-f pom.xml ' +
          '-Dsonar.projectKey=my:project ' +
		  '-Dsonar.projectName=My project ' +          
          '-Dsonar.language=java ' +
		  '-Dsonar.modules=app-java, app-groovy, app-it ' +
          '-Dsonar.sources=src/main ' +
          '-Dsonar.tests=src/test ' +
          '-Dsonar.binaries=target/classes '          
        }
    }
    }
}
