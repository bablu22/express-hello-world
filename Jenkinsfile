pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
        PATH = "/usr/local/bin:/usr/bin:/bin"
        APP_NAME = "express-hello-world"
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

        stage('Verify Environment') {
            steps {
                sh '''
                echo "Node version:"
                node -v
                echo "NPM version:"
                npm -v
                echo "PM2 path:"
                which pm2 || true
                '''
            }
        }

        stage('Deploy with PM2') {
            steps {
                sh '''
                echo "Deploying app with PM2..."

                if pm2 describe $APP_NAME > /dev/null 2>&1; then
                    echo "App exists → restarting"
                    pm2 restart $APP_NAME
                else
                    echo "App not found → starting new"
                    pm2 start index.js --name $APP_NAME
                fi

                pm2 save
                '''
            }
        }

        stage('Verify App') {
            steps {
                sh '''
                echo "PM2 process list:"
                pm2 list
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build & Deployment SUCCESS'
        }
        failure {
            echo '❌ Build FAILED'
        }
        always {
            echo '📦 Pipeline finished'
        }
    }
}
