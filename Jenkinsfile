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
                docker container run --restart always -d -p 5000:5000 --name web
                """
            }
        }
    }
}
