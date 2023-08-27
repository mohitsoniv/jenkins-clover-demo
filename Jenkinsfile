pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        
        stage('Build'){
            steps{
                echo 'Building Maven project'
                sh 'mvn clean compile'
            }
        }
        stage('Test'){
            steps{
                echo 'Building Maven project'
                sh 'mvn test'
            }
        }
    }
}
