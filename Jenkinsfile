pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image using the Dockerfile in the current directory
                    docker.build('my-docker-image')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container from the built image
                    docker.image('my-docker-image').run('-p 8000:8000')
                }
            }
        }
    }

    post {
        always {
            // Clean up: Stop and remove the Docker container
            script {
                docker.image('my-docker-image').stop()
                // docker.container('my-container').remove(force: true)
            }
        }
    }
}
