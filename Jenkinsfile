pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fintech-app .'
            }
        }

        stage('Stop Old Containers') {
    steps {
        sh '''
        docker ps -q --filter "name=fintech" | xargs -r docker stop
        docker ps -aq --filter "name=fintech" | xargs -r docker rm
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
