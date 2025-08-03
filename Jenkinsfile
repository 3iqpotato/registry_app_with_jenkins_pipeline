pipeline {
  agent {
    docker {
      image 'node:18'
      args '-u root'
      reuseNode true
    }
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'ls -la' // виждаш .git?
      }
    }
    stage('Install & Test') {
      steps {
        sh 'npm install'
        sh 'npm test'
      }
    }
  }
}
