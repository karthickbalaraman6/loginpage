pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/karthickbalaraman6/loginpage.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t login-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker ps -q --filter "name=login-app" | grep -q . && docker stop login-app && docker rm login-app || true
                docker run -d -p 5000:5000 --name login-app login-app
                '''
            }
        }
    }
}
