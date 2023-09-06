pipeline {
    agent {
      label 'slave'
      }
    environment {
        GIT_REPO_URL = 'https://github.com/roansar/jenkinsmains.git'
        MAVEN_TOOL = 'M3'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', 
                          branches: [[name: '*/master']], 
                          userRemoteConfigs: [[url: env.GIT_REPO_URL]]])
            }
        }

        stage('Build') {
            steps {
                // Compile your code (e.g., for a Java project)
                sh 'mvn clean compile'
            }
        }
        
        stage('Test') {
            steps {
                // Run tests (e.g., using JUnit)
                sh 'mvn test'
            }
        }
        
        stage('Package') {
            steps {
                // Package your application (e.g., create a JAR or WAR file)
                sh 'mvn package'
            }
        }
    }
    
    post {
        success {
            // You can perform actions if the pipeline succeeds
            echo 'Build successful! Deploying...'
            // Add deployment steps here
        }
        failure {
            // You can perform actions if the pipeline fails
            echo 'Build failed! Not deploying.'
        }
    }
}
