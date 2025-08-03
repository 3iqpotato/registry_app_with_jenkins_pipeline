pipeline {
    agent {
        docker {
            image 'node:18'  // Агент с Node.js 18
            args '-p 3000:3000'  // Ако приложението ползва порт 3000
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Извлича кода от Git (GitHub/GitLab/etc.)
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'  // Инсталира зависимости
            }
        }
        stage('Start App (Optional)') {
            steps {
                sh 'npm start &'  // Стартира приложението в background
                sleep(time: 5, unit: 'SECONDS')  // Изчаква 5 секунди
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'  // Пуска тестовете
            }
        }
    }
    post {
        always {
            sh 'pkill -f "npm start" || true'  // Спира приложението (ако е пуснато)
        }
    }
}