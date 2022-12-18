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
                sh 'mvn test -X'
            }
        }
    }
}