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

        stage('Test Run') {
            steps {
                sh 'node index.js'
            }
        }
    }
}
