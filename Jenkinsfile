pipeline {
    agent any

    tools {
        maven 'Maven' // Assuming you have Maven configured as 'Maven' under Jenkins -> Global Tool Configuration
        git 'Default' // Assuming Git is installed and configured as 'Default' in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Stage: Build'
                    echo 'Task: Build the code using Maven'
                    echo 'Tool: Maven'
                    
                    // Use Maven to build
                    bat 'mvn clean install'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running Unit and Integration Tests'
                    bat 'mvn test'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Running Code Analysis'
                    bat 'mvn sonar:sonar'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Running Security Scan'
                    bat 'mvn dependency-check:check'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging'
                    bat 'echo "Deploying to staging server..."'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running Integration Tests on Staging'
                    bat 'echo "Running integration tests on staging server..."'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production'
                    bat 'echo "Deploying to production server..."'
                }
            }
        }
    }

    post {
        success {
            echo 'Build succeeded! Sending email...'
            emailext (
                subject: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: "Good news! Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' completed successfully. Please check the logs for details.",
                to: "mahsanaj323@gmail.com",
                attachLog: true
            )
        }
        failure {
            echo 'Build failed! Sending email...'
            emailext (
                subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: "Unfortunately, job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed. Please check the logs for details.",
                to: "mahsanaj323@gmail.com",
                attachLog: true
            )
        }
    }
}
