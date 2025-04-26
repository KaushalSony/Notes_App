pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'kaushalsoni/rails-app'
        DOCKER_CREDENTIALS_ID = 'c3291af2-f0a0-4e54-a3a8-f8cad9be7203'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/KaushalSony/Notes_App.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Push') {
            steps {
                withDockerRegistry([credentialsId: "${DOCKER_CREDENTIALS_ID}", url: '']) {
                    docker.image("${DOCKER_IMAGE}").push('latest')
                }
            }
        }
    }
}
