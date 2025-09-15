pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning the GitHub repository...'
                git 'https://github.com/sudo-subham/Portfolio-DEVOPS.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t portfolio-website .'
            }
        }

        stage('Run Docker Container') {
            steps {
                echo 'Running Docker Container...'
                // Stop and remove container if already running
                sh '''
                docker stop portfolio-container || true
                docker rm portfolio-container || true
                docker run -d -p 8080:80 --name portfolio-container portfolio-website
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
