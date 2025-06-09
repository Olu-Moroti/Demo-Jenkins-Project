pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the repository...'
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Nginx container...'
                sh 'docker pull nginx:latest'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying Nginx container...'
                sh 'docker run -d --name nginx_app -p 80:80 nginx:latest'
            }
        }
        
        stage('Verify') {
            steps {
                echo 'Checking container status...'
                sh 'docker ps | grep nginx'
            }
        }
        
        stage('Cleanup') {
            steps {
                echo 'Cleaning up old containers...'
                sh 'docker stop nginx_app || true'
                sh 'docker rm nginx_app || true'
            }
        }
    }
}
