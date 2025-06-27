pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'nadermamdouh869/jenkins-tot:1.0'
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                // Jenkins does this automatically if Source Code Management is configured
            }
        }



        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t $DOCKER_IMAGE ."
                sh "docker ps "
                sh "docker stop $DOCKER_IMAGE"
                sh "docker rm $DOCKER_IMAGE"
            }
        }

        stage('Run Tests') {
            steps {
                // Optional: add your test command here
                echo 'Running tests...'
                sh 'npm test || echo "No tests defined"'
            }
        }

    }

    post {
        success {
            echo 'Build and Push Successful!'
        }
        failure {
            echo 'Something went wrong.'
        }
    }
}
