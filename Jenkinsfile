pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'git@github.com:10Fahim/flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop flask-app-container || true'
                sh 'docker rm flask-app-container || true'
                sh 'docker run -d --name flask-app-container -p 5000:5000 flask-app'
            }
        }
    }
}
