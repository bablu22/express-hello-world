pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/bablu22/express-hello-world.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Start App with PM2') {
            steps {
                sh '''
                pm2 delete express-hello-world || true
                pm2 start index.js --name express-hello-world
                pm2 save
                '''
            }
        }

        stage('Verify App') {
            steps {
                sh 'pm2 list'
            }
        }
    }

    post {
        success {
            echo '✅ App deployed and running with PM2'
        }
    }
}
