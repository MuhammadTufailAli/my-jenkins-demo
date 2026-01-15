pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Semgrep security scan'
                bat 'semgrep scan --config=auto --error'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Running build'
                bat 'npm run build'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
