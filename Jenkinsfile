pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/3iqpotato/registry_app_with_jenkins_pipeline'
            }
        }
        stage('Build & Test') {
            steps {
                sh 'npm install'
                sh 'npm run build'
                sh 'npm test'  // ако има тестове
            }
        }
        stage('Clean Workspace') {
            steps {
                cleanWs()  // изчиства workspace-а след билда
            }
        }
    }
}