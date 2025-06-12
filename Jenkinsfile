pipeline {
    agent any

    environment {
        IMAGE = "dockers1:latest"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Cleanup old container') {
            steps {
                script {
                    sh 'docker stop dockers1 || true'
                    sh 'docker rm dockers1 || true'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.IMAGE)
                }
            }
        }
        stage('Deploy Container') {
            steps {
                script {
                    docker.image(env.IMAGE).run('-d -p 8081:80 --name dockers1')
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}

