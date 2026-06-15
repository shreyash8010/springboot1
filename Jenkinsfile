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
                    cp target/ROOT.war /var/lib/tomcat10/webapps/
                    systemctl restart tomcat10
                '''
            }
        }
    }
}
