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
        stage('Deploy') {
            steps {
                // Pull Docker images
                sh 'docker pull azza463/myapp:latest'
                sh 'docker pull nginx:latest'
                
                // Start services using Docker Compose
                sh 'docker-compose up -d'
            }
        }
        stage('Push to GitHub') {
            steps {
                sh 'git status'
                // Add and commit changes
                sh 'git add .'
                sh 'git commit -m "ss"'
                
                // Push changes to GitHub
                sh 'git push origin main'
            }
        }
    }
}

