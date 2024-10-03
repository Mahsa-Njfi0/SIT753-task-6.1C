pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
            post {
                always {
                    // Save the build log
                    archiveArtifacts artifacts: 'build.log', allowEmptyArchive: true
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests...'
            }
            post {
                success {
                    mail to: 'mahsanaj323@gmail.com',
                         subject: "Pipeline Success: Unit and Integration Tests",
                         body: "The Unit and Integration Tests stage has completed successfully."
                }
                failure {
                    mail to: 'mahsanaj323@gmail.com',
                         subject: "Pipeline Failure: Unit and Integration Tests",
                         body: "The Unit and Integration Tests stage has failed. Please check the Jenkins logs for details."
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
                    mail to: 'mahsanaj323@gmail.com',
                         subject: "Pipeline Success: Security Scan",
                         body: "The Security Scan stage has completed successfully."
                }
                failure {
                    mail to: 'mahsanaj323@gmail.com',
                         subject: "Pipeline Failure: Security Scan",
                         body: "The Security Scan stage has failed. Please check the Jenkins logs for details."
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

    post {
        always {
            // Send the build.log file via email after the pipeline completes
            emailext (
                to: 'mahsanaj323@gmail.com',
                subject: "Pipeline Build Log: ${currentBuild.currentResult}",
                body: "Please find the attached build log file for the pipeline run.",
                attachLog: true,  // Attach the build log to the email
                compressLog: true  // Compress the log before sending if it's large
            )
        }
    }
}
//test
//test1
