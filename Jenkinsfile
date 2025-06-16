pipeline {
    agent any

    environment {
        IMAGE_NAME = 'hello-world-image'
        TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Docker Installation') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${TAG}", ".")
                }
            }
        }

        // Optional: Add more stages like push, run, cleanup
    }

    post {
        success {
            echo "✅ Build completed successfully!"
        }
        failure {
            echo "❌ Build failed. Check logs for details."
        }
    }
}
