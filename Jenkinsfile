pipeline{
    agent any

    tools{
        nodejs "nodejs"
    }

    stages{
        stage('SCM Checkout'){
            steps{
                git branch:'main', credentialsId:'github', url:'https://github.com/PraveenReddy2510/3-Tier-Full-Stack.git'
            }
        }
        // issues faces in above stage
        // 1. missed comma after credentialsId.
        // 2.
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