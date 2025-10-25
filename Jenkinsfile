pipeline {
    agent any

    environment {
        IMAGE_NAME = "simple-rest-api"
        IMAGE_TAG = "1.0"
    }

    stages {
        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker stop simple-rest-api || true && docker rm simple-rest-api || true'
                    sh 'docker run -d -p 8080:8080 --name simple-rest-api simple-rest-api:1.0'
                }
            }
        }
    }
}
