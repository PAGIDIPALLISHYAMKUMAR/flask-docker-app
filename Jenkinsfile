pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/PAGIDIPALLISHYAMKUMAR/flask-docker-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true
                docker run -d -p 5000:5000 --name flask-container flask-app
                '''
            }
        }
    }
}
