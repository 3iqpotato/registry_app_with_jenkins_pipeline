pipeline {
    agent any

    tools {
        nodejs 'node-24.5'  // Това трябва да е точното име от Global Tool Configuration
    }

    triggers {
        pollSCM('*/2 * * * *')  // Проверява за нови комити на всеки 2 минути
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/3iqpotato/registry_app_with_jenkins_pipeline.git'
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
