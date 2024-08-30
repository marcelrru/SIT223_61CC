pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Tool: Maven
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Tools: JUnit, TestNG, Mockito, Selenium
            }
            post {
                always {
                    emailext subject: "Job '${env.JOB_NAME}' (${env.BUILD_NUMBER}) - Unit and Integration Tests",
                             body: """Stage: Unit and Integration Tests
                             Status: ${currentBuild.currentResult}
                             See logs for more details.""",
                             to: 'marcelru27@gmail.com',
                             attachmentsPattern: '**/*.log'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Running Code Analysis...'
                // Tool: SonarQube
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Tool: OWASP Dependency-Check
            }
            post {
                always {
                    emailext subject: "Job '${env.JOB_NAME}' (${env.BUILD_NUMBER}) - Security Scan",
                             body: """Stage: Security Scan
                             Status: ${currentBuild.currentResult}
                             See logs for more details.""",
                             to: 'marcelru27@gmail.com',
                             attachmentsPattern: '**/*.log'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Tool: AWS CLI, Docker
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Tools: JUnit, Selenium
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Tool: AWS CLI, Docker
            }
        }
    }
}

