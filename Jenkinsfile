pipeline {
    agent any
    stages {
        stage('Setup') {
            steps {
                sh 'python -m venv venv'
                sh './venv/Scripts/pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh './venv/Scripts/python -m unittest discover tests'
            }
        }
        stage('Run') {
            steps {
                sh './venv/Scripts/python app.py'
            }
        }
    }
}
