pipeline {
    agent any

    environment {
        IMAGE_NAME = "nodejs-app"
        CONTAINER_NAME = "nodejs-container"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code checked out from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER_NAME || true
                docker run -d \
                  --name $CONTAINER_NAME \
                  -p 3000:3000 \
                  $IMAGE_NAME
                '''
            }
        }

    }
}
