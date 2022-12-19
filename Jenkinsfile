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
                sh 'mvn clean install -Dmaven.compiler.source=1.8 -Dmaven.compiler.target=1.8'
            }
        }
        stage('Static code analysis'){
            
            steps{
                
                script{
                    
                    withSonarQubeEnv(credentialsId: 'sonarqube-token') {
                        
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }        
    }
}
