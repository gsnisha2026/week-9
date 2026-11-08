
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Week 9 project checked out from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t kubdemoapp:v1 .'
            }
        }

            stage('Login to Docker Hub') {
            steps {
               
                   bat 'docker login -u nisha1310 -p <Gsnisha2023>'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker tag kubdemoapp:v1 nisha1310/simple-demo:kubeimage1'
                bat 'docker push nisha1310/simple-demo:kubeimage1'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
