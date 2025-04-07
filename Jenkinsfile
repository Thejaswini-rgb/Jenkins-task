pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Thejaswini-rgb/Jenkins-task.git'
            }
        }

        stage('Build') {
            steps {
                sh 'zip -r site.zip *.html'
            }
        }

        stage('Test') {
            steps {
                sh 'grep "<title>" index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Skipping actual deploy step (no remote server configured)'
            }
        }
    }
}
