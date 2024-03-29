pipeline {
     environment {
         dockerimagename = "ashurawat123/nodeapp"
         dockerImage = ""
     }
     
     agent any
     
     stages { 
         
         stage('Checkout Source') {
             steps {
                 git 'https://github.com/rawatarvind/micro1.git'
             }
         }
         
         stage('Build image') {
             steps{
                 script {
                     dockerImage = docker.build dockerimagename
                 }
             }
         }
         
         stage('Pushing Image') {
             environment {
                 registryCredential = 'dockerhublogin'
             }
            steps{
                script {
                    docker.withRegistry('https://registry.hub.docker.com', registryCredential ) {
                        dockerImage.push("latest")
                    }
                }
            }
         }
         
         stage('Deploying App to Kubernetes') {
             steps {
                 script {
                     kubernetesDeploy(configs: "deployment.yaml",kubeconfigId: "minikube")
                 }
             }
         }
}
