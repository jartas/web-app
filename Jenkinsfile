pipeline {
  agent any
stages {
stage(‘Build’) {
steps {
git 'https://github.com/jartas/web-app.git'
sh 'docker build -t jartas/webapp:${BUILD_NUMBER} .'
}
}
stage(‘Push’) {
steps {
withCredentials([usernamePassword(credentialsId: ‘docker-hub’, usernameVariable: ‘DOCKER_USERNAME’, passwordVariable: ‘DOCKER_PASSWORD’)]) {
sh ‘docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD’
sh ‘docker push jartas/webapp:${BUILD_NUMBER}’
}
}
}
}
}
