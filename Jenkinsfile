pipeline {
    agent any

    stages {

        stage('Pull Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t docker-jenkins-demo:v1 .'
            }
        }

        stage('Display Image Details') {
            steps {
                sh 'docker images docker-jenkins-demo'
                sh "docker image inspect docker-jenkins-demo:v1 --format='RepoTags={{.RepoTags}} Size={{.Size}} bytes'"
            }
        }
    }
}
