pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vcjain/jenkins-clover-demo.git']])
            }    
        }
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
                junit '**/target/surefire-reports/*.xml'
                clover cloverReportDir: 'target/site/clover', cloverReportFileName: 'clover.xml', failingTarget: [conditionalCoverage: 10, methodCoverage: 10, statementCoverage: 10], healthyTarget: [conditionalCoverage: 80, methodCoverage: 70, statementCoverage: 80], unhealthyTarget: [conditionalCoverage: 10, methodCoverage: 10, statementCoverage: 10]
            }
        }
    }
}
