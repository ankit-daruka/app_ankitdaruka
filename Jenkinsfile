pipeline {
    agent any 
      tools {
        maven "Maven3"
        jdk "OpenJDK-11" 
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
                withSonarQubeEnv(installationName:'Test_Sonar', credentialsId:'SonarQubeToken') {
                 sh 'mvn -X clean package sonar:sonar'
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