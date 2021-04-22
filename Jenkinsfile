pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                echo 'hello'
            }
        }
        stage('Compile') { 
            steps {

                sh "mvn clean compile"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test site"
            }
            
             post {
                always {
                    junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'   
                }
            }     
        }

        stage('Deploy') { 
            steps {
                sh "mvn package"
            }
        }
