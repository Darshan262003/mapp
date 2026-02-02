pipeline {
    agent any

    environment {
        IMAGE_NAME = "darshu262003/t3"
        DOCKER_HUB=credentials('dockerid')
    }

    stages {

        stage('checkout') {
            steps {
                git url: "https://github.com/Darshan262003/mapp.git",
                    branch: "main"
            }
        }

        stage('build') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerid') {
                        dockerImage.push()
                    }
                }
            }
            
        }
         
    }
}
