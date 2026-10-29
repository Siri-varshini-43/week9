pipeline {
 agent any
 stages {
 stage('Build Docker Image') {
 steps {
 echo 'Building Docker Image...'

 bat 'docker build -t week9 .'
 }
 }
 stage('Docker Login') {
 steps {
 bat 'docker login -u sirivarshini43 -p Siri@2006'
 }
 }
 stage('push Docker Image to Docker Hub') {
 steps {
 echo 'push Docker Image to Docker Hub'
 bat 'docker tag week9 sirivarshini43/week9:latest'
 bat 'docker push sirivarshini43/week9:latest'
 }
 }
 stage('Deploy to Kubernetes') {
 steps {
 bat 'kubectl apply -f deployment.yaml --validate=false'
 bat 'kubectl apply -f service.yaml'
 }
 }
 }
 post {
 success {
 echo 'Pipeline completed successfully!'

 }
 failure {
 echo 'Pipeline failed. Please check the logs.'
 }
 }
}