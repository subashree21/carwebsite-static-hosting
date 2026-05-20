pipeline {
    agent any

    environment {
        IMAGE_NAME = "suba-carwebsite-jenkins"
        AWS_ACCOUNT_ID = "198023436378"
        AWS_REGION = "us-east-1"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                credentialsId: 'github-creds',
                url: 'https://github.com/subashree21/carwebsite-static-hosting.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t suba-carwebsite-jenkins:v1 .'
            }
        }

        stage('Tag Docker Image') {
            steps {
                sh 'docker tag suba-carwebsite-jenkins:v1 198023436378.dkr.ecr.us-east-1.amazonaws.com/jenkins-repo:v1'
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region us-east-1 | \
                docker login --username AWS --password-stdin \
                198023436378.dkr.ecr.us-east-1.amazonaws.com
                '''
            }
        }

        stage('Push Image to ECR') {
            steps {
                sh 'docker push 198023436378.dkr.ecr.us-east-1.amazonaws.com/jenkins-repo:v1'
            }
        }
    }
}
