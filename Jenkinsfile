pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f demo-container || true'
                sh 'docker run -d -p 5000:5000 --name demo-container myapp:latest'
            }
        }
    }

    post {
        success {
            emailext (
                subject: 'Build SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}',
                body: 'Job ${JOB_NAME} build #${BUILD_NUMBER} was successful!',
                to: 'abunaeem059322@gmail.com'
            )
        }
        failure {
            emailext (
                subject: 'Build FAILED: ${JOB_NAME} #${BUILD_NUMBER}',
                body: 'Job ${JOB_NAME} build #${BUILD_NUMBER} failed!',
                to: 'abunaeem059322@gmail.com'
            )
        }
    }
}



