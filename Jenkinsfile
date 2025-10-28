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
                sh 'docker build -t loginpage .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker ps -q --filter "name=loginpage" | grep -q . && docker stop loginpage && docker rm loginpage || true
                docker run -d -p 5000:5000 --name loginpage loginpage
                '''
            }
        }
    }
}
