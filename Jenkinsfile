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
            steps {
                 script {
                def scannerHome = tool 'SonarQubeScanner';
                tools {
                        jdk "JDK 11" 
                    }
                withSonarQubeEnv('Test_Sonar') {
                 sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=sonar-ankitdaruka'
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