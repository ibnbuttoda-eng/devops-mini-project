pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Repository already checked out by Jenkins.'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-web:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop myweb || true
                docker rm myweb || true
                docker run -d --name myweb -p 80:80 devops-web:v1
                '''
            }
        }

    }
}