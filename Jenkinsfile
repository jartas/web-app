pipeline {
    agent any

    triggers {
        cron('H/15 * * * *')
    }
    parameters {
        choice(name: 'environment', choices: ['dev', 'test', 'prod'], description: 'Select environment to deploy')
    }
    stages {
        stage ('Print') {
            steps {
                echo "Hello Devops Engineers"
            }
        }
    }

    post {
        success {
            echo 'Pipilena was successfully deployed'
        }
        failure {
            echo 'Something is wrong, check logs'
        }
    }
}
