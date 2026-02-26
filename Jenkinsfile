pipeline {
    agent any
    
    environment {
        IMAGE_NAME = "rajshreec/train-app"
        IMAGE_TAG = "v${BUILD_NUMBER}"
        APP_SERVER = "ubuntu@Server ID"
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/RJ-Chaudhari/cicd-pipeline-train-schedule-pipelines.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE_NAME:$IMAGE_TAG'
            }
        }


         stage('Deploy to App Server') {
            steps {
                sh """
                 ssh -o StrictHostKeyChecking=no $APP_SERVER '
                 cd compose-app &&
                export IMAGE_TAG=$IMAGE_TAG &&
                docker compose pull &&
                docker compose up -d
                '
                """
            }
        }
    }
}
