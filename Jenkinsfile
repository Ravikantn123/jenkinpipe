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
                git branch: 'main', url: 'https://github.com/Ravikantn123/java-Ptoject.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                // Ensure Dockerfile exists in the correct location
                sh 'docker build -t node-app -f /var/lib/jenkins/workspace/cicdpipe/node_project .'
                
            }
        }

        stage('Deploy to EC2 Agent') {
            steps {
                echo 'Deploying to EC2 Agent...'
                // Add deployment commands here
                sh 'docker run -d -p 8000:8000 node-app'
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
