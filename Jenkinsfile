pipeline {
    agent any
    
    stages {
        // Шаг 1: Получить код из Git
        stage('Get Code') {
            steps {
                echo '📦 Getting code from Git...'
                checkout scm
            }
        }
        
        // Шаг 2: Установить зависимости
        stage('Install') {
            steps {
                echo '📥 Installing dependencies...'
                bat 'npm install'
            }
        }
        
        // Шаг 3: Запустить тесты
        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                bat 'npm test'
            }
        }
        
        // Шаг 4: Собрать приложение
        stage('Build') {
            steps {
                echo '🔨 Building application...'
                bat 'npm run build'
            }
        }
    }
    
    // Что делать после выполнения
    post {
        success {
            echo '✅ Everything is OK!'
        }
        failure {
            echo '❌ Something failed!'
        }
    }
}