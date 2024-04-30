pipeline {
    agent any

    stage('Checkout') {
    steps {
        // Récupérer le code depuis le dépôt GitHub
        git url: 'https://github.com/azza-12/azza.git', branch: 'main'
    }
}


        stage('Deploy') {
            steps {
                // Tirer l'image Docker 'myapp' depuis Docker Hub
                sh 'docker pull azza463/myapp:latest'

                // Tirer l'image Docker 'nginx' depuis Docker Hub
                sh 'docker pull nginx:latest'

                // Exécuter Docker Compose pour déployer les services
                sh 'docker-compose up -d'
            }
        }

        stage('Push to GitHub') {
            steps {
                // Ajouter et committer les modifications
                sh 'git add .'
                sh 'git commit -m "Update deployment"'

                // Poussez les modifications vers le dépôt GitHub
                sh 'git push'
            }
        }
    }


