pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'node-app' // Replace with your desired image name
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/Ravikantn123/java-Ptoject.git'
                // Replace with your GitHub repository URL and branch name
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh """
                cd node_project
                docker build -t $DOCKER_IMAGE .
                """
            }
        }

        stage('Deploy to EC2 Agent') {
            steps {
                echo 'Deploying on EC2 agent...'
                sh """
                # Run the new Docker container
                docker run -d --name Node-container -p 8000:8000 $DOCKER_IMAGE
                """
                // Replace `your-container-name` and port mappings as necessary
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
