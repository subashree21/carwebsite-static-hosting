pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/subashree21/carwebsite-static-hosting.git'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                rm -rf /var/www/html/*
                cp -r index.html style.css script.js images /var/www/html/
                '''
            }
        }
    }
}
