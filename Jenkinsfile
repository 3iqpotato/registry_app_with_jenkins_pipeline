pipeline {
    agent any

    stages {
        // 1. Checkout code
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        // 2. Verify Node.js (без инсталация)
        stage('Verify Node.js') {
            steps {
                sh '''
                    if ! command -v node &> /dev/null; then
                        echo "ERROR: Node.js не е инсталиран!"
                        echo "Трябва да инсталирате Node.js в Jenkins контейнера ръчно:"
                        echo "1. docker exec -itu root jenkins-docker bash"
                        echo "2. curl -fsSL https://deb.nodesource.com/setup_18.x | bash -"
                        echo "3. apt-get install -y nodejs"
                        exit 1
                    fi
                    node --version
                    npm --version
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