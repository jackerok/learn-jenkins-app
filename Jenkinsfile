pipeline {
    agent any
    
    stages {
        // Шаг 1: Получить код из Git
        stage('Checkout') {
            steps {
                echo '📦 Checking out code from Git...'
                checkout scm
            }
        }
        
        // Шаг 2: Установить зависимости
        stage('Install Dependencies') {
            steps {
                echo '📥 Installing npm dependencies...'
                bat 'npm install'
            }
        }
        
        // Шаг 3: Запустить тесты
        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                // --watchAll=false чтобы не зависло
                bat 'npm test -- --watchAll=false'
            }
        }
        
        // Шаг 4: Собрать приложение
        stage('Build Application') {
            steps {
                echo '🔨 Building React application...'
                bat 'npm run build'
            }
        }
        
        // Шаг 5: Архивировать результат сборки
        stage('Archive Build') {
            steps {
                echo '📦 Archiving build artifacts...'
                archiveArtifacts artifacts: 'build/**/*', allowEmptyArchive: true
            }
        }
    }
    
    // Действия после выполнения pipeline
    post {
        success {
            echo '✅ Pipeline completed successfully!'
            echo '🎉 Build artifacts are ready in the build/ folder'
        }
        
        failure {
            echo '❌ Pipeline failed!'
            echo '📋 Check the console output for errors'
        }
        
        always {
            echo '🏁 Pipeline execution finished'
            echo "Build Number: ${env.BUILD_NUMBER}"
            echo "Branch: ${env.BRANCH_NAME ?: 'main'}"
        }
    }
}