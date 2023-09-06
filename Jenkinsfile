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
                /
