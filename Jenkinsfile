pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using Maven or Gradle as a build automation tool.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit tests using JUnit, and integration tests using TestNG.'
            }
            post {
                success {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-unit-tests.txt"
                        writeFile file: logFile, text: currentBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Success: Unit and Integration Tests",
                             body: "The Unit and Integration Tests stage has completed successfully. Logs are attached.",
                             attachmentsPattern: logFile
                    }
                }
                failure {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-unit-tests.txt"
                        writeFile file: logFile, text: currentBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Failure: Unit and Integration Tests",
                             body: "The Unit and Integration Tests stage has failed. Logs are attached.",
                             attachmentsPattern: logFile
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Performing static code analysis using SonarQube to check code quality and compliance.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Running a security scan using OWASP ZAP to identify vulnerabilities in the code.'
            }
            post {
                success {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-security-scan.txt"
                        writeFile file: logFile, text: currentBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Success: Security Scan",
                             body: "The Security Scan stage has completed successfully. Logs are attached.",
                             attachmentsPattern: logFile
                    }
                }
                failure {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-security-scan.txt"
                        writeFile file: logFile, text: currentBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Failure: Security Scan",
                             body: "The Security Scan stage has failed. Logs are attached.",
                             attachmentsPattern: logFile
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying the application to a staging server using AWS EC2.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests in the staging environment using Selenium.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying the application to a production server using AWS EC2.'
            }
        }
    }
}
