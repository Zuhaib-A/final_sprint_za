pipeline {
    agent any

    stages {
        stage('Build Front-End') {
            steps {
                script {
                    // Checkout your front-end code from your repository
                    checkout scm

                    // Build the front-end Docker image
                    sh 'docker build -t za-front-end-image -f lbg-car-react-starter/Dockerfile .'
                }
            }
        }

        stage('Build Back-End') {
            steps {
                script {
                    // Checkout your back-end code from your repository
                    checkout scm

                    // Build the back-end Docker image
                    sh 'docker build -t za-back-end-image -f lbg-car-spring-app-starter/Dockerfile .'
                }
            }
        }

        stage('Deploy Containers') {
            steps {
                script {
                    // Deploy the front-end container
                    sh 'docker run -d -p 80:80 front-end-image'

                    // Deploy the back-end container
                    sh 'docker run -d -p 8080:8080 back-end-image'
                }
            }
        }
    }
}