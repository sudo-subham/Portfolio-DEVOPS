pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t portfolio-website .'
            }
        }

        stage('Run Docker Container') {
            steps {
                echo 'Running Docker Container...'
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
            echo 'Pipeline finished.'
        }
    }
}
