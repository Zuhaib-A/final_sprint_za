pipeline {
    agent any

    stages {
        stage('Build Front-End') {
            steps {
                script {
                    checkout scm
                    dir('final_sprint_za/lbg-car-react-starter') {
                        sh 'docker build -t za-front-end-image .'
                    }
                }
            }
        }

        stage('Deploy Front-End') {
            steps {
                sh 'docker run -d -p 80:80 za-front-end-image'
            }
        }

        stage('Build Back-End') {
            steps {
                script {
                    checkout scm
                    dir('final_sprint_za/lbg-car-spring-app-starter') {
                        sh 'docker build -t za-back-end-image .'
                    }
                }
            }
        }

        stage('Deploy Back-End') {
            steps {
                sh 'docker run -d -p 81:81 za-back-end-image'
            }
        }
    }
}