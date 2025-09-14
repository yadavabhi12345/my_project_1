pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-python-app"
        DOCKERHUB_USERNAME = "yoyoyadav123"
        TAG = "latest"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/yadavabhi12345/my_project_1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${TAG}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        dockerImage.push()
                    }
                }
            }
        }

        // Optional: Add test or deployment stages here later
    }
}
