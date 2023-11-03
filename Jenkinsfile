pipeline {
    agent any
    stages {
        stage('Build and Deploy Containers') {
            steps {
                script {
                    // Checkout your code from the repository
                    checkout scm

                    // Build and deploy front-end
                    dir('final_sprint_za/lbg-car-react-starter') {
                        sh 'docker build -t za-front-end-image -f Dockerfile .'
                        sh 'docker run -d -p 80:80 za-front-end-image'
                    }

                    // Build and deploy back-end
                    dir('final_sprint_za/lbg-car-spring-app-starter') {
                        sh 'docker build -t za-back-end-image -f Dockerfile .'
                        sh 'docker run -d -p 81:81 za-back-end-image'
                    }
                }
            }
        }
    }
}