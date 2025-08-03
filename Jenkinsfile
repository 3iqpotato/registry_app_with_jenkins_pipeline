pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Environment') {
            steps {
                sh '''
                    # Проверка за Node.js
                    if ! command -v node &> /dev/null; then
                        echo "ERROR: Node.js не е инсталиран!"
                        exit 1
                    fi
                    
                    # Проверка за npm
                    if ! command -v npm &> /dev/null; then
                        echo "ERROR: npm не е инсталиран!"
                        exit 1
                    fi
                    
                    echo "Версии:"
                    node --version
                    npm --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }
}