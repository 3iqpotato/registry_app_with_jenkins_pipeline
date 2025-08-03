pipeline {
    agent any

    stages {
        stage('Setup Environment') {
            steps {
                sh '''#!/bin/bash -l
                    # Изтегляне и инсталиране на Node.js в home директория
                    mkdir -p ~/.nodejs
                    curl -L https://nodejs.org/dist/v18.20.2/node-v18.20.2-linux-x64.tar.xz | tar -xJ -C ~/.nodejs --strip-components=1
                    echo "export PATH=\$HOME/.nodejs/bin:\$PATH" >> ~/.bashrc
                    source ~/.bashrc
                    
                    node --version
                    npm --version
                '''
            }
        }

        stage('Run Pipeline') {
            steps {
                sh '''#!/bin/bash -l
                    source ~/.bashrc
                    npm install
                    npm test
                '''
            }
        }
    }
}