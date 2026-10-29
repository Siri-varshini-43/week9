
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t week9 .'
            }
        }
        stage('Docker login') {
            steps {
                echo 'login to docker hub...'
                bat 'docker login -u sirivarshini43 -p sAhi@2002'
            }
        }
        stage('push Docker image to Docker Hub') {
            steps {
                echo 'pushing image to hub...'
                bat 'docker tag week6 sirivarshini43/week9:week9'
                bat 'docker push sirivarshini43/week9:week9'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                echo 'Deploying to Kubernetes...'
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
        always {
            echo 'Jenkins pipeline execution completed.'
        }
    }
}
