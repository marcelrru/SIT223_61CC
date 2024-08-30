pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                sh 'echo "Build log" > build.log'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Performing Unit and Integration Tests using JUnit, TestNG, Mockito, and Selenium...'
                sh 'echo "Test log" > test.log'
            }
            post {
                always {
                    script {
                        // Archive log files
                        archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true

                        // Determine the status of the stage
                        def status = currentBuild.currentResult

                        // Send email with logs attached
                        emailext(
                            subject: "Stage Status Email - Unit and Integration Tests ${status}",
                            body: """\
                                Stage: Unit and Integration Tests
                                Status: ${status}
                                """,
                            to: 'marcelru27@gmail.com',
                            attachmentsPattern: '**/*.log'
                        )
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis using SonarQube...'
                sh 'echo "Code Analysis log" > code-analysis.log'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan using OWASP Dependency-Check...'
                sh 'echo "Security Scan log" > security-scan.log'
            }
            post {
                always {
                    script {
                        // Archive log files
                        archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true

                        // Determine the status of the stage
                        def status = currentBuild.currentResult

                        // Send email with logs attached
                        emailext(
                            subject: "Stage Status Email - Security Scan ${status}",
                            body: """\
                                Stage: Security Scan
                                Status: ${status}
                                """,
                            to: 'marcelru27@gmail.com',
                            attachmentsPattern: '**/*.log'
                        )
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS CLI and Docker...'
                sh 'echo "Deploy to Staging log" > deploy-staging.log'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging using JUnit and Selenium...'
                sh 'echo "Integration Tests log" > integration-tests.log'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production using AWS CLI and Docker...'
                sh 'echo "Deploy to Production log" > deploy-production.log'
            }
        }
    }
}
