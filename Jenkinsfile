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