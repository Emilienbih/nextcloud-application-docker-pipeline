pipeline {

    tools{

        maven 'maven3.9.2'
    }
    agent any

    environment {
        registry = "391405332002.dkr.ecr.ca-central-1.amazonaws.com/testing1"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Lion-Technology-Solutions/nextcloud-application-docker-pipeline.git']])
            }
        }
        
        stage ("Build Image") {
            steps {
                script {
                    dockerImage = docker.build registry
                    dockerImage.tag("$BUILD_NUMBER")
                }
            }
        }
        
        stage ("Push to ECR") {
            steps {
                script {
                    sh 'aws ecr get-login-password --region ca-central-1 | docker login --username AWS --password-stdin 391405332002.dkr.ecr.ca-central-1.amazonaws.com'
                    sh 'docker push 391405332002.dkr.ecr.ca-central-1.amazonaws.com/testing1:$BUILD_NUMBER'
                    
                }
            }
        }    
    }
}