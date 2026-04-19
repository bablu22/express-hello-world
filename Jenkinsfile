pipeline{
    agent any

    stages{
        state("Checkout"){
            steps{
                git "https://github.com/bablu22/express-hello-world.git"
            }
        }

        stage("Install dependencies"){
            steps{
                sh "npm install"
            }
        }

        stage("Run App"){
            steps{
                sh "npm start"
            }
        }
    }
}
