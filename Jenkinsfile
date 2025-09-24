pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sujoth666/project0"  // Your Docker Hub repo
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sujoth6/project0.git'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-cred-id', // Replace with your Jenkins credential ID
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "📦 Building Docker image..."
                    sh "docker build -t ${DOCKER_IMAGE}:${BUILD_NUMBER} ."
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "🧪 Running container for quick test..."
                    sh "docker run -d --name test_container_${BUILD_NUMBER} -p 5000:5000 ${DOCKER_IMAGE}:${BUILD_NUMBER}"
                    sh "sleep 5"
                    sh "docker ps | grep test_container_${BUILD_NUMBER}"
                    sh "docker stop test_container_${BUILD_NUMBER}"
                    sh "docker rm test_container_${BUILD_NUMBER}"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    echo "⬆️ Pushing Docker image..."
                    sh "docker push ${DOCKER_IMAGE}:${BUILD_NUMBER}"
                    sh "docker tag ${DOCKER_IMAGE}:${BUILD_NUMBER} ${DOCKER_IMAGE}:latest"
                    sh "docker push ${DOCKER_IMAGE}:latest"
                }
            }
        }
    }

    post {
        success {
            echo "✅ Successfully built and pushed ${DOCKER_IMAGE}:${BUILD_NUMBER} and :latest"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
}

