pipeline {
    agent any

    tools {
        maven 'maven-3.9.10' //
    }

    stages {
        stage('Build & Test') {
            steps {
                sh 'mvn clean test' //exécute les tests
            }
        }

        stage('Publish Test Results') {
            steps {
                junit 'target/surefire-reports/*.xml' //analyse les fichiers XML de test (produits automatiquement par Maven)
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/surefire-reports/*.xml', fingerprint: true //archive les rapports pour consultation
        }
    }
}
