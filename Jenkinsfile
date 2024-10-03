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
}
//test
//test1

