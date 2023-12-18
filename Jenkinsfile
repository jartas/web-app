pipeline {
environment {
registry = "jartas/web-app"
registryCredential = '041803c2-b86c-4638-aa47-4c4e441d7baa'
dockerImage = ''
}
      parameters {
        choice(name: 'environment', choices: ['dev', 'uat', 'prod'], description: 'Select environment to deploy')
    }
agent any
stages {
        stage ('Print') {
            steps {
                echo "Hello Devops Engineers"
            }
        }
    }
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
sh "docker stop $registry:$BUILD_NUMBER | true"
sh "docker rm $registry:$BUILD_NUMBER | true"
sh "docker run --name web-app -d -p 5001:5000 $registry:$BUILD_NUMBER"
}
}
}
post {
        success {
            echo 'Application was successfully deployed'
        }
        failure {
            echo 'Something is wrong, please check logs'
        }
}
