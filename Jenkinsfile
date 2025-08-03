pipeline {
    agent {
        docker {
            image 'node:18'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Автоматично извлича кода
            }
        }
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}