pipeline {
    agent any
 
    environment {
        IMAGE_NAME = "jenkins-demo-app"
        CONTAINER_NAME = "jenkins-docker-container"
    }
 
    stages {
 
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }
 
        stage('Build') {
            steps {
                echo 'Build Stage Started...'
                sh 'ls -la'
            }
        }
 
        stage('Test') {
            steps {
                echo 'Testing application...'
                sh 'test -f index.html'
                echo 'Test Passed'
            }
        }
 
        stage('Docker Build') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t ${IMAGE_NAME}:latest .'
            }
        }
 
        stage('Docker Run') {
            steps {
                echo 'Running Docker Container...'
 
                // Remove old container if it exists
                sh 'docker rm -f ${CONTAINER_NAME} || true'
 
                // Run new container
                sh 'docker run -d --name ${CONTAINER_NAME} -p 8081:80 ${IMAGE_NAME}:latest'
 
                // Check running container
                sh 'docker ps'
            }
        }
    }
 
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
 
        failure {
            echo 'Pipeline failed!'
        }
    }
}
