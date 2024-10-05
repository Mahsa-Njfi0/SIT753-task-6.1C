pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using a build automation tool...'
                echo 'Tool: Maven or equivalent build tool'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                echo 'Tool: JUnit for Unit Tests, Selenium for Integration Tests'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis to ensure code meets standards...'
                echo 'Tool: SonarQube'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Scanning code for security vulnerabilities...'
                echo 'Tool: OWASP Dependency Check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to Staging environment...'
                echo 'Tool: SSH/SCP or AWS CLI for deployment'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging environment...'
                echo 'Tool: Selenium or equivalent integration testing tool'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to Production environment...'
                echo 'Tool: AWS CLI or SSH/SCP'
            }
        }
    }

    environment {
        EMAIL_RECIPIENTS = 'mahsanaj323@gmail.com'
    }

    post {
        success {
            emailext(
                subject: "Build ${currentBuild.fullDisplayName} - SUCCESS",
                body: "The pipeline ${currentBuild.fullDisplayName} has completed successfully.",
                to: "${env.EMAIL_RECIPIENTS}",
                attachLog: true
            )
        }
        failure {
            emailext(
                subject: "Build ${currentBuild.fullDisplayName} - FAILURE",
                body: "The pipeline ${currentBuild.fullDisplayName} has failed. Please check the attached log.",
                to: "${env.EMAIL_RECIPIENTS}",
                attachLog: true //tsey
            )
        }
    }
}
