pipeline {
    environment {
        dockerimagename = "ashurawat123/nodeapp"
        dockerImage = ""
        registryCredential = 'dockerhublogin'
    }
     
    agent any
     
    stages { 
        stage('Checkout Source') {
            steps {
                git 'https://github.com/rawatarvind/micro1.git'
            }
        }
         
        stage('Build image') {
            steps {
                script {
                    dockerImage = docker.build dockerimagename
                }
            }
        }
         
        stage('Pushing Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', registryCredential) {
                        dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
