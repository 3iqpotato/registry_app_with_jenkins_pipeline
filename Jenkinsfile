pipeline {
    agent any  // Checkout да е извън контейнер
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test in Docker') {
            agent {
                docker {
                    image 'node:18'
                    args '-u root'  // ако трябва root за инсталация
                }
            }
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }
    }
}
