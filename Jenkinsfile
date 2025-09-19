pipeline {
    agent any

    environment {
        WEB_ROOT = '/var/www/html'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Récupération du code source"
                checkout scm
            }
        }
        stage('Deploy') {
            steps {
                echo "Déploiement de l'application"
                sh 'cp -r * /var/www/html/'
            }
        }
        stage('Test') {
            steps {
                echo "Vérification du déploiement"
                sh 'curl -f http://localhost/'
            }
        }
    }

    post {
        success {
            echo "Déploiement réussi"
        }

        failure {
            echo "Le déploiement a échoué"
        }
        
        always {
            echo "Nettoyage"
            sh "rm -rf ${WEB_ROOT}/"
        }
    }
}