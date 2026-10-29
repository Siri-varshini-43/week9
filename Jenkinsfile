pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t sirivarshini43/week9 .'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'sirivarshini43',
                    passwordVariable: 'Siri@2006'
                )]) {
                    bat 'docker login -u "%DOCKER_USER%" -p "%DOCKER_PASS%"'
                    bat 'docker push sirivarshini43/week9:latest'
                }
            }
        }

        stage('Deploy') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
}
