pipeline {
    agent any
    environment {
        IMAGE_NAME = "myapp"
        IMAGE_TAG = "latest"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }
        stage('Run Container') {
            steps {
                
                sh "docker rm -f demo-container || true" 
                sh "docker run -d -p 5000:5000 --name demo-container ${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }
    }
}
