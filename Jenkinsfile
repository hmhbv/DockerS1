pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/hmhbv/DockerS1.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-nginx .'
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:80 --name nginx-container my-nginx'
                }
            }
        }
    }
}
