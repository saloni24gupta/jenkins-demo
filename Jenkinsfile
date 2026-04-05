pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                sh 'docker build -t my-app .'
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker stop my-container || true'
                sh 'docker rm my-container || true'
                sh 'docker run -d -p 8086:80 --name my-container my-app'
            }
        }
    }
}
