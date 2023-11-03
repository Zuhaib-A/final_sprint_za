pipeline {
    agent any

    stages {
        stage('Build Front-End') {
            steps {
                checkout scm
                sh 'docker build -t za-front-end-image -f lbg-car-react-starter/Dockerfile .'
            }
        }

        stage('Build Back-End') {
            steps {
                checkout scm
                sh 'docker build -t za-back-end-image -f lbg-car-spring-app-starter/Dockerfile .'
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