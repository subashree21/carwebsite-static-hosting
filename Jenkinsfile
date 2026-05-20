pipeline {
    agent any

    stages {

        stage('Deploy') {
            steps {
                echo 'Deploying website to Nginx'

                sh '''
                rm -rf /var/www/html/*
                cp -r *.html css images js /var/www/html/ || true
                '''
            }
        }
    }
}
