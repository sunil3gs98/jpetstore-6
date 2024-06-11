pipeline {
    agent any
    tools{
        jdk 'java17'
        maven 'maven3'
    }
    environment{
       SCANNER_HOME = tool 'sonar-scanner'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'dev', url: 'https://github.com/sunil3gs98/secretsanta-generator-sunil.git'
            }
        }
        stage('Code-Compile') {
            steps {
                sh "mvn clean compile"
                
            }
        }
        stage('Test cases') {
            steps {
                sh "mvn test"
                
            }
        }
        stage('Sonarqube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=spring-pet-store \
                   -Dsonar.branch.name=dev \
                   -Dsonar.java.binaries=. \
                   -Dsonar.projectKey=pet '''
                }
                
                
            }
        }
        stage('Build Application') {
            steps {
                sh "mvn clean package"
            }
        }
        
        
        
       
        
    
        
    }
}
