
pipeline {
    agent any
    stages {
        stage('Clone github Repo') {
            steps {
                sh '''
                git clone https://github.com/oadeoyeo/web-app.git
                '''
            }
        }
        stage('Build docker image') {
            steps {
                sh '''
                docker build -t oxer-html:v01 .
                '''
            }
        }
        stage('Push image to Dockerhub') {
            steps {
                sh '''
                docker push oxer-html:v01
                '''
            }
        }
    }
}