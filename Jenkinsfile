pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/bablu22/express-hello-world.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run App') {
            steps {
                sh 'npm start'
            }
        }
    }
}
