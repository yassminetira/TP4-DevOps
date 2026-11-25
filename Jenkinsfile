
pipeline {
    agent any

    stages {

        stage('Checkout GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yassminetira/TP4-DevOps.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                bat 'docker compose build'
            }
        }

        stage('Deploy Containers') {
            steps {
                bat 'docker compose up -d'
            }
        }

        stage('Test Application') {
            steps {
                bat 'docker compose ps'
                bat 'docker compose logs server'
                bat 'curl.exe --fail --retry 10 --retry-delay 3 --retry-connrefused http://localhost:9000/api/health'
                bat 'curl.exe --fail --retry 10 --retry-delay 3 --retry-connrefused http://localhost:3000'
            }
        }

        stage('Show Docker Images') {
            steps {
                bat 'docker images'
            }
        }
    }

    post {
        success {
            echo 'Pipeline TP4 execute avec succes !'
        }

        failure {
            echo 'Erreur pendant execution du pipeline.'
        }
    }
}
