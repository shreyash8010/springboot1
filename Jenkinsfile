pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/shreyash8010/springboot1.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r target/ROOT/* /var/www/html/
                    sudo systemctl restart apache2
                '''
            }
        }
    }
}
