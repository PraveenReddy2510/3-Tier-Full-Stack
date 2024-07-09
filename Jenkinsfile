pipeline{
    agent any

    stages{
        stage('SCM Checkout'){
            steps{
                git branch:'main', credentialsId:'github', url:'https://github.com/PraveenReddy2510/3-Tier-Full-Stack.git'
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}