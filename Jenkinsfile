pipeline {
environment {
registry = "jartas/web-app"
registryCredential = '041803c2-b86c-4638-aa47-4c4e441d7baa'
dockerImage = ''
}
agent any
stages {
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential, ghcr.io ) {
dockerImage.push()
}
}
}
}
stage('Cleaning up') {
steps{
sh "docker rmi $registry:$BUILD_NUMBER"
}
}
}
}
