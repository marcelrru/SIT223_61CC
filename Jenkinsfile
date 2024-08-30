pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Simulate build and create log file
                sh 'echo "Build log" > build.log'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Performing Unit and Integration Tests using JUnit, TestNG, Mockito, and Selenium...'
                // Simulate test and create log file
                sh 'echo "Test log" > test.log'
            }
            post {
                success {
                    script {
                        // Archive log files
                        archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true

                        // Send email with logs attached
                        emailext(
                            subject: "Stage Status Email - Unit and Integration Tests Success",
                            body: """\
                                Stage: Unit and Integration Tests
                                Status: Success
                                """,
                            to: 'marcelru27@gmail.com',
                            attachmentsPattern: '**/*.log',
                            attachLog: false
                        )
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis using SonarQube...'
                // Simulate code analysis and create log file
                sh 'echo "Code Analysis log" > code-analysis.log'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP Dependency-Check...'
                // Simulate security scan and create log file
                sh 'echo "Security Scan log" > security-scan.log'
            }
            post {
                success {
                    script {
                        // Archive log files
                        archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true

                        // Send email with logs attached
                        emailext(
                            subject: "Stage Status Email - Security Scan Success",
                            body: """\
                                Stage: Security Scan
                                Status: Success
                                """,
                            to: 'marcelru27@gmail.com',
                            attachmentsPattern: '**/*.log',
                            attachLog: false
                        )
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS CLI and Docker...'
                // Simulate deployment and create log file
                sh 'echo "Deploy to Staging log" > deploy-staging.log'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging using JUnit and Selenium...'
                // Simulate integration tests and create log file
                sh 'echo "Integration Tests log" > integration-tests.log'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production using AWS CLI and Docker...'
                // Simulate deployment and create log file
                sh 'echo "Deploy to Production log" > deploy-production.log'
            }
        }
    }
}
