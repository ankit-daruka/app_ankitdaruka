pipeline {
    agent any 
      tools {
        maven "Maven3"
        jdk "JDK 9"
        sonarscan "SonarQubeScanner"
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
                withSonarQubeEnv('Test_Sonar') {
                 sh 'mvn clean package sonar:sonar'
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