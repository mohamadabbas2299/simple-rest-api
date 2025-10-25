pipeline {
    agent any

    stages {
        stage('Build Maven Project') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t simple-rest-api .'
            }
        }
        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 8080:8080 simple-rest-api'
            }
        }
    }
}
