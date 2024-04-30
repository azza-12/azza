pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git 'https://github.com/azza-12/azza.git' , branch: 'main'
            }
        }
        stage('Deploy') {
            steps {
                // Pull Docker images
                sh 'docker pull votrenomutilisateur/myapp:latest'
                sh 'docker pull nginx:latest'
                
                // Start services using Docker Compose
                sh 'docker-compose up -d'
            }
        }
        stage('Push to GitHub') {
            steps {
                // Add and commit changes
                sh 'git add .'
                sh 'git commit -m "Update deployment"'
                
                // Push changes to GitHub
                sh 'git push origin main'
            }
        }
    }
}

