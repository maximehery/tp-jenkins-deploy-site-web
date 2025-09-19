pipeline {
    agent any

    environment {
        WEB_ROOT = '/var/www/html'
        BACKUP_DIR = '/var/www/html.backup'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Récupération du code source'
                checkout scm
            }
        }

        stage('Backup') {
            steps {
                echo 'Sauvegarde du site actuel'
                sh 'sudo cp -r ${WEB_ROOT} ${BACKUP_DIR} || true'
            }
        }

        stage('Deploy') {
            steps {
                echo "Déploiement de l'application"
                sh 'sudo cp -r * /var/www/html/'
            }
        }

        stage('Test') {
            steps {
                echo 'Vérification du déploiement'
                sh 'curl -f http://localhost/'
            }
        }
    }

    post {
        success {
            echo 'Déploiement réussi'
        }

        failure {
            echo 'Le déploiement a échoué'
        }

        always {
            echo 'Nettoyage'
            sh 'sudo rm -rf ${BACKUP_DIR} || true'
        }
    }
}
