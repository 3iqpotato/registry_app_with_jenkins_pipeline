pipeline {
    agent any

    stages {
        stage('Build inside Docker') {
            steps {
                script {
                    docker.image('node:18').inside('-u root') {
                        checkout scm
                        sh 'git status'     // тестово
                        sh 'npm install'
                        sh 'npm test'
                    }
                }
            }
        }
    }
}
