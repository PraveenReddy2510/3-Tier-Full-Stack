pipeline{
    agent any

    tools{
        nodejs "nodejs"
        sonar
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
                dir ('backend'){
                    sh "npm install"
                }
            }
        }
        // issues faces in above stage
        // 1. missed to include tools installed step above
        // 2.
        stage('building npm app'){
            steps{
                dir ('backend'){
                    sh "npm run build"
                }
            }
        }

        stage('testing npm app'){
            steps{
                dir ('backend'){
                    sh "npm run test"
                }
            }
        }

        stage('Run SonarQube Analysis') {
            steps {
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-server') {
                        // Run SonarQube analysis for backend
                        dir('backend') {
                            sh 'sonar-scanner -Dsonar.projectKey=my-backend-project -Dsonar.sources=. -Dsonar.exclusions=**/node_modules/**'
                        }

                        // Run SonarQube analysis for frontend if applicable
                        dir('frontend') {
                            sh 'sonar-scanner -Dsonar.projectKey=my-frontend-project -Dsonar.sources=. -Dsonar.exclusions=**/node_modules/**'
                        }
                    }
                }
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}