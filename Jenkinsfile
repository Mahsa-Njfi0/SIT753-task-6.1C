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
                    emailext(
                        to: 'mahsanaj323@gmail.com',
                        subject: "Pipeline: Test Stage - Success",
                        body: "The Test stage has succeeded.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'mahsanaj323@gmail.com',
                        subject: "Pipeline: Test Stage - Failure",
                        body: "The Test stage has failed. Please review the attached logs.",
                        attachLog: true
                    )
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
                    emailext(
                        to: 'mahsanaj323@gmail.com',
                        subject: "Pipeline: Security Scan - Success",
                        body: "The Security Scan stage has succeeded.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'mahsanaj323@gmail.com',
                        subject: "Pipeline: Security Scan - Failure",
                        body: "The Security Scan stage has failed. Please review the attached logs.",
                        attachLog: true
                    )
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
