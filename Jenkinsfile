pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fintech-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop fintech || true
                docker rm fintech || true
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker run -d --name fintech -p 8081:80 fintech-app'
            }
        }
    }
}
