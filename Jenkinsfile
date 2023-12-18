pipeline {
    agent any
    stages {
        def path = tool name: 'gradle-4.7', type: 'gradle'
        stage('Build') {
            agent {
                docker {
                    image 'redis'
                    // Run the container on the node specified at the
                    // top-level of the Pipeline, in the same workspace,
                    // rather than on a new node entirely:
                    reuseNode true
                }
            }
            steps {
                sh 'gradle --version'
            }
        }
    }
}
