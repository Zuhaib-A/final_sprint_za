pipeline {
    environment {
        registry = "zuhaibali/sprintproject"
        registryCredentials = "dockerhub-credentials"
        dockerImage = ""
    }
    
    agent any
    
    stages {
        stage('Build Front-End') {
            steps {
                script {
                    dir('final_sprint_za/lbg-car-react-starter') {
                        dockerImage = docker.build(registry)
                    }
                }
            }
        }

        stage('Push Front-End to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', registryCredentials) {
                        dockerImage.push("${env.BUILD_NUMBER}-front-end")
                        dockerImage.push("latest-front-end")
                    }
                }
            }
        }

        stage('Build Back-End') {
            steps {
                script {
                    dir('final_sprint_za/lbg-car-spring-app-starter') {
                        dockerImage = docker.build(registry)
                    }
                }
            }
        }

        stage('Push Back-End to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', registryCredentials) {
                        dockerImage.push("${env.BUILD_NUMBER}-back-end")
                        dockerImage.push("latest-back-end")
                    }
                }
            }
        }
    }
}