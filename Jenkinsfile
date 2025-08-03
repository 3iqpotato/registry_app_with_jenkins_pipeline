pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS-LTS' // Трябва да съвпада с името от стъпка 2
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