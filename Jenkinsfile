pipeline {
    agent any
    
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true  // <-- ДОБАВИТЬ ЭТО
                }
            }
            steps {
                sh 'npm --version'
                sh 'npm ci'
                sh 'npm run build'
            }
        }
    }
}