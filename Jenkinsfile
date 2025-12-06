pipeline {
    agent {
        docker { image 'python:3.10' }
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'python -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh './venv/bin/python -m pytest tests/'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t secureapp .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy your app here'
            }
        }
    }
}
