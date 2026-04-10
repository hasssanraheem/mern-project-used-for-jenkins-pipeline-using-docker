pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/hasssanraheem/registration-and-login-application-with-crud-operation-using-MERN-stack.git'
            }
        }

        stage('Build & Deploy with Docker') {
            steps {
                sh 'docker-compose -f docker-compose.jenkins.yml down || true'
                sh 'docker-compose -f docker-compose.jenkins.yml up -d'
            }
        }

        stage('Verify') {
            steps {
                sh 'sleep 10'
                sh 'docker ps | grep backend-ci'
                sh 'docker ps | grep frontend-ci'
                sh 'docker ps | grep mongodb-ci'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed! App running on ports 3001 and 2001.'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
