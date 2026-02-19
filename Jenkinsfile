pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/RJ-Chaudhari/cicd-pipeline-train-schedule-pipelines.git'
            }
        }

        stage('Install Node Dependencies') {
            steps {
                sh 'npm install'
            }
        }

     stage('Start Application') {
            steps {
                sh 'nohup npm start > app.log 2>&1 &'
            }
        }
    }
}
