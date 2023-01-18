pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..a'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh """
                docker run --rm -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock --group-add=$(stat -c %g /var/run/docker.sock) jenkinsci/docker-workflow-demo
                """
            }
        }
    }
}
