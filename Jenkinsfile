pipeline {
    agent any

    environment { 
        NAME = 'vignesh'
    }

    triggers {
        cron('H/15 * * * *')
    }

    parameters {
        choice(name: 'environment', choices: ['dev', 'uat', 'prod'], description: 'Select environment to deploy')
    }

    stages {
        stage ('Print') {
            environment { 
                MESSAGE = 'Hello Devops Engineers'
            }
            steps {
                echo "$MESSAGE"
            }
        }
    }

    post {
        success {
            echo 'I will say Hello only if job is success'
        }
        failure {
            echo 'I will say Hello only if job is failure'
        }
    }
}
