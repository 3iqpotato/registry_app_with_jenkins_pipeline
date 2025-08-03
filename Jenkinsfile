pipeline {
    agent any

    stages {
        // 1. Checkout code
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        // 2. Setup Node.js (ако не е инсталиран)
        stage('Setup Node.js') {
            steps {
                sh '''
                    if ! command -v node &> /dev/null; then
                        echo "Installing Node.js..."
                        curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
                        apt-get install -y nodejs
                    fi
                    node --version
                '''
            }
        }

        // 3. Install dependencies
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        // 4. Start application (ако има server.js/index.js)
        stage('Start App') {
            when {
                expression { fileExists('server.js') || fileExists('index.js') }
            }
            steps {
                sh 'npm start &'
                sh 'sleep 5'
            }
        }

        // 5. Run tests
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            echo "Build completed - ${currentBuild.result ?: 'SUCCESS'}"
        }
    }
}