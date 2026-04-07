pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Mohith1823/Docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t loginpage .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop login-container || true
                docker rm login-container || true
                docker run -d -p 8082:80 --name login-container loginpage
                '''
            }
        }
    }
}
