pipeline {
    agent any

    stages {
        stage('Build Front-End') {
            steps {
                dir('lbg-car-react-starter') {
                    checkout scm
                    sh 'docker build -t za-front-end-image -f /Dockerfile .'
                }
            }
        }

        stage('Build Back-End') {
            steps {
                dir('lbg-car-spring-app-starter') {
                    checkout scm
                    sh 'docker build -t za-back-end-image -f /Dockerfile .'
                }
            }
        }

        stage('Deploy Containers') {
            steps {
                sh 'docker run -d -p 80:80 za-front-end-image'
                sh 'docker run -d -p 81:81 za-back-end-image'
            }
        }
    }
}