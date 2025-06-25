pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/ilierrazi00/my-next-app.git'
      }
    }

    stage('Install') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -f Dockerfile.prod -t my-next-app-prod .'
      }
    }
  }

  post {
    success {
      echo 'Pipeline terminé avec succès !'
    }
    failure {
      echo 'Échec du pipeline.'
    }
  }
}
