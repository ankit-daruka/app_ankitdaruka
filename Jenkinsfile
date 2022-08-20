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
            }
        }
        stage('Test case execution') { 
             tools {
                        jdk "openjdk-11" 
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