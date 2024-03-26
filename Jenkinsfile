pipeline {
    agent any

    stages {
        stage('Deploy Pod') {
            agent {
                kubernetes {
                    yaml """
                    apiVersion: v1
                    kind: Pod
                    metadata:
                      name: my-pod
                    spec:
                      containers:
                      - name: nginx
                        image: nginx
                    """
                }
            }
            steps {
                sh 'echo hello > /usr/share/nginx/html/index.html'
            }
        }
    }
}
