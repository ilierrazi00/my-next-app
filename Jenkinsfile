pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ilierrazi00/my-next-app.git'
            }
        }

        stage('Install') {
            steps {
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                bat 'npm run test'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-next-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 3000:3000 my-next-app'
            }
        }
    }

    post {
        failure {
            echo 'Échec du pipeline.'
        }
    }
}
