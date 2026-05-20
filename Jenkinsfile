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
                sudo rm -rf /var/www/html/*
                sudo cp -r index.html css js images /var/www/html/ || true
                sudo systemctl restart nginx
                '''
            }
        }
    }
}
