pipeline {
    agent any

    stages {
        stage('Setup Node.js') {
            steps {
                sh '''#!/bin/bash -l
                    # Инсталиране на Node.js глобално
                    curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
                    sudo apt-get install -y nodejs
                    
                    # Проверка на версиите
                    echo "Node.js version: $(node --version)"
                    echo "npm version: $(npm --version)"
                '''
            }
        }

        stage('Install & Test') {
            steps {
                sh '''#!/bin/bash -l
                    # Изрично задаване на PATH (ако е необходимо)
                    export PATH=$PATH:/usr/bin
                    
                    # Инсталиране и тестване
                    npm install
                    npm test
                '''
            }
        }
    }
}