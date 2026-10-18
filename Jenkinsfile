pipeline {
    agent any

    stages {
        stage('Pull Code from GitHub') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-web-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f my-web-container || true'
                sh 'docker run -d --name my-web-container -p 80:80 my-web-app'
            }
        }
    }
}
