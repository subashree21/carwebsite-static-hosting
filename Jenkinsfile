pipeline {
    agent any

    stages {

        stage('Deploy Application') {
            steps {
                sh '''
                rm -rf /var/www/html/*
                cp -r *.html css images js /var/www/html/
                '''
            }
        }
    }
}
