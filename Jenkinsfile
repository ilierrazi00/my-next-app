pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/ton-repo.git', branch: 'main' // Remplace par ton vrai dépôt ou commente si local
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
