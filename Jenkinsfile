pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                sh 'echo "Build log: Build started" > build.log'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Performing Unit and Integration Tests using JUnit, TestNG, Mockito, and Selenium...'
                sh 'echo "Unit Tests log: All tests passed" > test.log'
            }
            post {
                success {
                    script {
                        // Read log file content
                        def logContent = readFile('test.log')
                        
                        // Send email with log content in the body
                        mail to: 'marcelru27@gmail.com',
                             subject: 'Stage Status Email - Unit and Integration Tests Success',
                             body: """\
                                 Stage: Unit and Integration Tests
                                 Status: Success
                                 
                                 Logs:
                                 ${logContent}
                                 """
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis using SonarQube...'
                sh 'echo "Code Analysis log: Analysis complete" > code-analysis.log'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP Dependency-Check...'
                sh 'echo "Security Scan log: Scan complete" > security-scan.log'
            }
            post {
                success {
                    script {
                        // Read log file content
                        def logContent = readFile('security-scan.log')
                        
                        // Send email with log content in the body
                        mail to: 'marcelru27@gmail.com',
                             subject: 'Stage Status Email - Security Scan Success',
                             body: """\
                                 Stage: Security Scan
                                 Status: Success
                                 
                                 Logs:
                                 ${logContent}
                                 """
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS CLI and Docker...'
                sh 'echo "Deploy to Staging log: Deployment successful" > deploy-staging.log'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging using JUnit and Selenium...'
                sh 'echo "Integration Tests log: All tests passed" > integration-tests.log'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production using AWS CLI and Docker...'
                sh 'echo "Deploy to Production log: Deployment successful" > deploy-production.log'
            }
        }
    }
}
