pipeline {
    environment {
    registry = "jartas/web-app"
    name = "web-app"
    registryCredential = '041803c2-b86c-4638-aa47-4c4e441d7baa'
    dockerImage = ''
    }
    agent any
        stages {
            stage('Building image') {
                steps{
                    script {
                        dockerImage = docker.build registry + ":$BUILD_NUMBER"
                    }
                }
            }
        stage('Push image') {
            steps{
                script {
                    docker.withRegistry( 'https://ghcr.io', registryCredential) {
                    dockerImage.push()
                    }
                }
            }
        }
        stage('Start applicaton') {
            steps{
                sh "docker stop $name| true"
                sh "docker rm $name| true"
                sh "docker run --name $name -d -p 5001:5000 $registry:$BUILD_NUMBER"
            }
        }
    }
}
