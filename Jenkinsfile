pipeline{
    agent any

    stages{
        stage('SCM Checkout'){
            steps{
                git branch:'main', credentialsId:'github', url:'https://github.com/PraveenReddy2510/3-Tier-Full-Stack.git'
            }
        }
        stage('installing dependencies'){
            steps{
                sh "npm install"
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}