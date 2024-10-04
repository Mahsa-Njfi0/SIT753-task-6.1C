pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests...'
            }
            post {
                success {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-unit-integration-tests.txt"
                        writeFile file: logFile, text: currentBuild.rawBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Success: Unit and Integration Tests",
                             body: "The Unit and Integration Tests stage has completed successfully. Logs are attached.",
                             attachmentsPattern: logFile
                    }
                }
                failure {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-unit-integration-tests.txt"
                        writeFile file: logFile, text: currentBuild.rawBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Failure: Unit and Integration Tests",
                             body: "The Unit and Integration Tests stage has failed. Logs are attached. Please check the Jenkins logs for details.",
                             attachmentsPattern: logFile
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
            }
            post {
                success {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-security-scan.txt"
                        writeFile file: logFile, text: currentBuild.rawBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Success: Security Scan",
                             body: "The Security Scan stage has completed successfully. Logs are attached.",
                             attachmentsPattern: logFile
                    }
                }
                failure {
                    script {
                        def logFile = "${env.WORKSPACE}/pipeline-log-security-scan.txt"
                        writeFile file: logFile, text: currentBuild.rawBuild.getLog(100).join("\n")
                        mail to: 'mahsanaj323@gmail.com',
                             subject: "Pipeline Failure: Security Scan",
                             body: "The Security Scan stage has failed. Logs are attached. Please check the Jenkins logs for details.",
                             attachmentsPattern: logFile
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
        }
    }
}
