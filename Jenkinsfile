pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/tarunre12/Deployment-using-tomcat-and-docker.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                  docker build -t charitize .
                '''
            }
        }

        stage('Deploy Docker Container') {
            steps {
                sh '''
                  docker stop venu || true
                  docker rm venu || true

                  docker run -d --name webapp -p 1122:8080 charitize
                '''
            }
        }
    }
}
