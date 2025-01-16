pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                git 'https://github.com/Ravikantn123/java-Ptoject.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                // Ensure Dockerfile exists in the correct location
                sh 'cd /var/lib/jenkins/workspace/cicdpipe/node_project && docker build -t node-app .'
            }
        }

        stage('Deploy to EC2 Agent') {
            steps {
                echo 'Deploying to EC2 Agent...'
                // Add deployment commands here
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
