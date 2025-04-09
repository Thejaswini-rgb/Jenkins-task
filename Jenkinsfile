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
                echo 'Zipping HTML files...'
                sh 'zip -r site.zip *.html'
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic HTML test...'
                sh 'grep "<title>" index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Nginx Server via SCP...'
                sh '''
                    scp -o StrictHostKeyChecking=no -i ~/Downloads/nginx-key.pem site.zip ubuntu@13.218.128.42:/var/www/html/
                    ssh -o StrictHostKeyChecking=no -i ~/Downloads/nginx-key.pem ubuntu@13.218.128.42 "cd /var/www/html && unzip -o site.zip && rm site.zip"
                '''
            }
        }
    }
}
