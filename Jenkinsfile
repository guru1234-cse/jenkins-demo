pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t docker-jenkins-demo:v2 .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Docker container...'

                sh '''
                    docker rm -f ci-test-container 2>/dev/null || true

                    docker run -d \
                        --name ci-test-container \
                        -p 3001:3000 \
                        docker-jenkins-demo:v2

                    sleep 5

                    curl -f http://localhost:3001

                    docker rm -f ci-test-container
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'

                sh '''
                    docker rm -f docker-jenkins-demo-container 2>/dev/null || true

                    docker run -d \
                        --name docker-jenkins-demo-container \
                        -p 3000:3000 \
                        docker-jenkins-demo:v2

                    docker ps
                '''
            }
        }
    }
}
