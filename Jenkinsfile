pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupération du code
            }
        }
        stage('Deploy') {
            steps {
                // Copie des fichiers vers le serveur web
            }
        }
        stage('Test') {
            steps {
                // Vérification du déploiement
            }
        }
    }

    post {
        success {
            // Action en cas de succès (echo, ou autre)
        }

        failure {
            // Action en cas d'échec
        }
        always {
            // Nettoyage
        }
    }
}
