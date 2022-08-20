pipeline {
    agent any 
      tools {
        maven "Maven3"
        jdk "JDK 9"
    }
    stages {
        stage('Build') { 
            steps {
               sh 'mvn clean install'
               echo 'Building' 
               echo JAVA_HOME
               echo java --version
            }
        }
        stage('Test case execution') { 
             tools {
                        jdk "OpenJDK-11" 
                    }
            steps {
                 script {
                def scannerHome = tool 'SonarQubeScanner';
                withSonarQubeEnv('Test_Sonar') {
                 sh 'mvn -X clean verify sonar:sonar -Dsonar.projectKey=sonar-ankitdaruka'
            }
        }
                echo 'Test case execution'
            }
        }
        stage('Kubernetes Deployment') { 
            steps {
                echo 'Kubernetes Deployment'
            }
        }
    }
}