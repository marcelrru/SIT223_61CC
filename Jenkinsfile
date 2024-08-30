pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Simulate build process
                sh 'echo "Build started"'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Performing Unit and Integration Tests using JUnit, TestNG, Mockito, and Selenium...'
                // Simulate tests
                sh 'echo "Tests completed"'
            }
            post {
                success {
                    script {
                        def buildLog = currentBuild.rawBuild.log.join('\n')
                        mail to: "marcelru27@gmail.com",
                             subject: "Stage Status Email: Unit and Integration Tests",
                             body: """\
                             Stage: Unit and Integration Tests
                             Status: Success
                             Log:
                             ${buildLog}
                             """,
                             attachLog: true
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis using SonarQube...'
                // Simulate code analysis
                sh 'echo "Code analysis completed"'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP Dependency-Check...'
                // Simulate security scan
                sh 'echo "Security scan completed"'
            }
            post {
                success {
                    script {
                        def buildLog = currentBuild.rawBuild.log.join('\n')
                        mail to: "marcelru27@gmail.com",
                             subject: "Stage Status Email: Security Scan",
                             body: """\
                             Stage: Security Scan
                             Status: Success
                             Log:
                             ${buildLog}
                             """,
                             attachLog: true
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS CLI and Docker...'
                // Simulate deployment
                sh 'echo "Deployment to staging completed"'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging using JUnit and Selenium...'
                // Simulate integration tests
                sh 'echo "Integration tests on staging completed"'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production using AWS CLI and Docker...'
                // Simulate production deployment
                sh 'echo "Deployment to production completed"'
            }
        }
    }
}
