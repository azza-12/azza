pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git branch: 'main', url: 'https://github.com/azza-12/azza.git'
            }
        }
 stage('Test html site') {
            steps {
                  publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'jen.html', reportName: 'HTML Report',                   reportTitles: '', useWrapperFileDirectly: true])
            }
        }
   stage('Build Docker Image') {
            steps {
                sh 'docker build -t web .'
            }
        } 
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 51:80 --name myapp1 web'
            }
        }
       
        stage('Push to Docker Hub') {
            steps {
                sh 'docker login -u azza463 -p azza@1234'
                sh 'docker tag web docker.io/azza463/web:latest'
                sh 'docker push docker.io/azza463/web:latest'
            }
        }
       
        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
