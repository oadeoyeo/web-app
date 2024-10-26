
pipeline {
    agent any
    stages {
        stage('Clone github Repo') {
            steps {
                git branch: 'main', credentialsId: 'git-creds', url: 'https://github.com/oadeoyeo/web-app.git'
            }
        }
        stage('Build docker image') {
            steps {
                script {
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        dir('HTML-APP') {
                            sh "                            
                            docker build -t oxer-html .
                            "
                        }                    
                    }
                }
            }
        }
        stage('Push image to Dockerhub') {
            steps {
                script {
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                   sh '''
                    docker push oadeoyeo/oxer-html:001
                    '''
                    }
                }
            }
        }
    }
}