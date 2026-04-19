pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url:'https://github.com/bablu22/express-hello-world.git', branch: 'main'
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
