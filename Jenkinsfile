pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'jagruti03shinde/flask-app:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', 'https://github.com/jagrutishinde03/jenkins-docker.git'  // Replace with your Git repository URL
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'ac5b2295-c06f-4770-9dec-2130e2e2ec4a') {
                        docker.image(DOCKER_IMAGE).push()
                    }
                }
            }
        }
    }
}
