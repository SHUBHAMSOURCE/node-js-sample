pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop node || true'
                sh 'docker rm node || true'
                sh 'docker run -d -p 3002:5000 --name node node-app'
            }
        }

        stage('Test') {
            steps {
                sh 'sleep 10'
                  curl 'http://host.docker.internal:3002'            
        }
    }
}
