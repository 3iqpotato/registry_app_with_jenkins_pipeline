pipeline {
    agent any  // Използва default Jenkins agent

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build in Docker') {
            agent {
                docker {
                    image 'node:18'
                    args '-p 3000:3000'
                }
            }
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }
    }
}
