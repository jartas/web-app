pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/jartas/web-app.git'
                sh 'docker build . -t ghcr.io/jartas/web-app:latest'
            }

        }
    }
}
