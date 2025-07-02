pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/yourusername/fastapi-docker.git'
            }
        }

        stage('Build Docker') {
            steps {
                sh 'sudo docker build -t fastapi-app .'
            }
        }

        stage('Deploy Docker') {
            steps {
                sh '''
                sudo docker stop fastapi-app || true
                sudo docker rm fastapi-app || true
                sudo docker run -d --name fastapi-app -p 8000:8000 fastapi-app
                '''
            }
        }
    }
}
