pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'flask-app:latest' // Use the repository name and tag
        DOCKER_REGISTRY = 'https://hub.docker.com/' // Docker Hub URL
        DOCKER_CREDENTIALS = 'NCL' // ID of your Docker credentials
    }
    
    stages {
        stage('Push Docker Image') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: "${DOCKER_CREDENTIALS}", passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        sh 'docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD} ${DOCKER_REGISTRY}'
                        sh 'docker tag ${DOCKER_IMAGE} ${DOCKER_REGISTRY}/${DOCKER_IMAGE}'
                        sh 'docker push ${DOCKER_REGISTRY}/${DOCKER_IMAGE}'
                    }
                }
            }
        }
    }
}

