pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Nginx...'

                sh '''
                rm -rf /var/www/html/*
                cp -r *.html css images js /var/www/html/ || true
                '''

                echo 'Deployment completed successfully'
            }
        }
    }
}
