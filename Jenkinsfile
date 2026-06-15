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

        stage('Deploy') {
            steps {
                sh '''
                    echo "Deploying Spring Boot application..."

                    pkill -f springboot1 || true

                    nohup java -jar target/*.jar > app.log 2>&1 &
                '''
            }
        }
    }
}
