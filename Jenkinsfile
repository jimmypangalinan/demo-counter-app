pipeline {

    agent any 

    stages{

        stage('Git Checkout'){

            steps{
                git 'https://github.com/jimmypangalinan/demo-counter-app.git'
            }
        }
        stage('Unit Testing'){

            steps{
                sh 'mvn test'
            }
        }
        stage('Integration Testing'){

            steps{
                sh 'mvn verify -DskiUnitTests'
            }
        }
        stage('Maven Build'){

            steps{
                sh 'mvn clean install'
            }
        }
        stage('SonarQube analysis'){
            steps {
                scripts{
                    // waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api-key'
                    withSonarQubeEnv(credentialsId: 'sonar-api-key') {
                    sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}