pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code checked out successfully'
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage completed successfully'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage completed successfully'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }
    }
}
