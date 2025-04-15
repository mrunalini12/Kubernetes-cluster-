pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-node-app"
        TAG = "v1"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/mrunalini12/Kubernetes-cluster-.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$TAG .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                        echo "$PASSWORD" | docker login -u "$USERNAME" --password-stdin
                        docker tag $IMAGE_NAME:$TAG $USERNAME/$IMAGE_NAME:$TAG
                        docker push $USERNAME/$IMAGE_NAME:$TAG
                    '''
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
