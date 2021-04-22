pipeline {
    agent any 
    stages {
        stage('Compile') { 
            steps {

                sh "mvn compile"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test"
            }
            
             post {
                always {
                    junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'   
                }
            }     
        }

        stage('Deploy') { 
            steps {
                sh "mvn deploy package"
            }
        }
