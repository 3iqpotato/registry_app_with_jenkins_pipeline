pipeline {
    agent {
        docker {
            image 'node:18'   // Използва официален Node.js Docker образ
            args '-u root:root'  // В случай че има нужда от root права
        }
    }

    environment {
        NODE_ENV = 'test'
    }

    stages {
        stage('Checkout code') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build (optional)') {
            when {
                expression { fileExists('build') || fileExists('webpack.config.js') }
            }
            steps {
                sh 'npm run build'
            }
        }

        stage('Start application (optional)') {
            when {
                expression { fileExists('server.js') || fileExists('index.js') }
            }
            steps {
                sh 'npm start &'
                sleep 5  // Изчакване за стартиране
            }
        }

        stage('Run tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Tests passed!'
        }
        failure {
            echo 'Tests failed.'
        }
    }
}
