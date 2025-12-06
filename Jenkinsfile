pipeline {
    agent any

    environment {
        IMAGE_NAME = "secureapp"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/atharvmalve/pythonn'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                sh './venv/bin/flake8 .'
            }
        }

        stage('Test') {
            steps {
                sh './venv/bin/pytest tests/'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Deploy') {
            steps {
                sh "docker run -d -p 5000:5000 ${IMAGE_NAME}:latest"
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
