pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                sh 'echo "Build started"'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Performing Unit and Integration Tests using JUnit, TestNG, Mockito, and Selenium...'
                sh 'echo "Tests completed"'
            }
            post {
                success {
                    mail to: "marcelru27@gmail.com",
                         subject: "Unit and Integration Tests - Success",
                         body: """\
                         Stage: Unit and Integration Tests
                         Status: Success
                         The build logs are attached.
                         """,
                         attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis using SonarQube...'
                sh 'echo "Code analysis completed"'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP Dependency-Check...'
                sh 'echo "Security scan completed"'
            }
            post {
                success {
                    mail to: "marcelru27@gmail.com",
                         subject: "Security Scan - Success",
                         body: """\
                         Stage: Security Scan
                         Status: Success
                         The build logs are attached.
                         """,
                         attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS CLI and Docker...'
                sh 'echo "Deployment to staging completed"'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging using JUnit and Selenium...'
                sh 'echo "Integration tests on staging completed"'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production using AWS CLI and Docker...'
                sh 'echo "Deployment to production completed"'
            }
        }
    }
}
