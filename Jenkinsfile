pipeline {
    agent any
    environment {
        NODEJS_VERSION = '24'  // 👈 Съвпада с версията в Jenkins глобалните настройки
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Автоматично използва вече конфигурирания Git repo
            }
        }

        stage('Setup Node') {
            steps {
                nodejs(nodeJSInstallationName: "node-${NODEJS_VERSION}") {
                    sh 'node --version && npm --version'
                }
            }
        }

        stage('Install & Test') {
            steps {
                sh 'npm install'
                sh 'npm test'  // 👈 Задължително имайте тестове в package.json!
            }
        }
    }
}