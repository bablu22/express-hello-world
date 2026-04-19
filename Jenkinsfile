pipeline {
    agent any

    environment {
        CI = 'true'
        NODE_ENV = 'production'
    }

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/bablu22/express-hello-world.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install --no-audit --no-fund'
            }
        }

        stage('Verify Node') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Test Run (CI Safe)') {
            steps {
                sh 'node index.js'
            }
        }
    }

    post {
        success {
            echo '✅ Build SUCCESS'
        }
        failure {
            echo '❌ Build FAILED'
        }
        always {
            echo '📦 Pipeline finished'
        }
    }
}
