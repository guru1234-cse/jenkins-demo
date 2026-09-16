pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker Compose application...'
                sh 'docker compose build'
            }
        }

        stage('Test') {
            steps {
                echo 'Validating Docker Compose configuration...'
                sh 'docker compose config'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application using Docker Compose...'
                sh 'docker compose up -d'
                sh 'sleep 10'
                sh 'docker compose ps'
                sh 'curl -f http://localhost:8081'
                sh 'curl -f http://localhost:3001'
            }
        }
    }
}
