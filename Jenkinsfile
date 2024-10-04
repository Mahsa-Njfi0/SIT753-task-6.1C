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

    post {
        success {
            echo 'Pipeline completed successfully!'
            emailext(
                subject: 'Pipeline Success',
                body: 'The pipeline has succeeded!',
                to: 'mahsanaj323@gmail.com',
                from: 'mahsa.njfi0@gmail.com', // Set the custom "From" address here
                attachLog: true
            )
        }
        failure {
            echo 'Pipeline failed!'
            emailext(
                subject: 'Pipeline Failed',
                body: 'The pipeline has failed. Please check the logs.',
                to: 'mahsanaj323@gmail.com',
                from: 'mahsa.njfi0@gmail.com', // Set the custom "From" address here
                attachLog: true
            )
        }
    }
}
