pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Запускаем Docker контейнер и выполняем команды внутри
                    bat '''
                        docker run --rm ^
                        -v "%WORKSPACE%":/app ^
                        -w /app ^
                        node:18-alpine ^
                        sh -c "npm --version && npm ci && npm run build"
                    '''
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    bat '''
                        docker run --rm ^
                        -v "%WORKSPACE%":/app ^
                        -w /app ^
                        node:18-alpine ^
                        sh -c "npm test"
                    '''
                }
            }
        }
    }
}