pipeline {
    agent any

    tools {
        git 'Default'  // Specify the Git tool here, the one you configured in Global Tool Configuration
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Use Maven to build the application
                sh 'mvn clean install'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Use JUnit for Unit Testing and Selenium for Integration Testing
                sh 'mvn test'
                sh 'mvn integration-test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                // Use SonarQube for code quality checks
                sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Use OWASP Dependency Check to scan for security vulnerabilities
                sh 'dependency-check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to AWS EC2 (using Ansible or custom script)
                sh 'ansible-playbook deploy-staging.yml'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run integration tests on the staging environment (Selenium)
                sh 'mvn verify -Denv=staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy to production server
                sh 'ansible-playbook deploy-prod.yml'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            // Send an email on success (use Jenkins Email Extension plugin)
            emailext subject: 'Build Success',
                     body: 'The build was successful',
                     attachLog: true,
                     to: 'mahsanaj323@gmail.com'
        }
        failure {
            echo 'Pipeline failed!'
            // Send an email on failure (use Jenkins Email Extension plugin)
            emailext subject: 'Build Failure',
                     body: 'The build failed. Please check the logs.',
                     attachLog: true,
                     to: 'mahsanaj323@gmail.com'
        }
    }
}
