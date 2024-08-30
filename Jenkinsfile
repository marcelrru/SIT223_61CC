pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Performing Unit and Integration Tests using JUnit, TestNG, Mockito, and Selenium...'
            }
            post {
                success {
                    mail to: "marcelru27@gmail.com",
                    subject: "Stage Status Email",
                    body: """\
                    Stage: Unit and Integration Tests
                    Status: Success
                    """
                }
                
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis using SonarQube...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP Dependency-Check...'
            }
            post {
               success {
                    mail to: "marcelru27@gmail.com",
                    subject: "Stage Status Email",
                    body: """\
                    Stage: Security Scan
                    Status: Success
                    """
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS CLI and Docker...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging using JUnit and Selenium...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production using AWS CLI and Docker...'
            }
        }
    }
}

