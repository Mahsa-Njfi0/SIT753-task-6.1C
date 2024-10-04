pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Platform-aware build command
                script {
                    if (isUnix()) {
                        sh 'mvn clean install' // Unix/Linux shell command
                    } else {
                        bat 'mvn clean install' // Windows batch command
                    }
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                script {
                    if (isUnix()) {
                        sh 'mvn test'
                    } else {
                        bat 'mvn test'
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                script {
                    if (isUnix()) {
                        sh 'sonar-scanner'
                    } else {
                        bat 'sonar-scanner'
                    }
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                script {
                    if (isUnix()) {
                        sh 'dependency-check'
                    } else {
                        bat 'dependency-check'
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                script {
                    if (isUnix()) {
                        sh 'ansible-playbook deploy-staging.yml'
                    } else {
                        bat 'ansible-playbook deploy-staging.yml'
                    }
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                script {
                    if (isUnix()) {
                        sh 'mvn verify -Denv=staging'
                    } else {
                        bat 'mvn verify -Denv=staging'
                    }
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                script {
                    if (isUnix()) {
                        sh 'ansible-playbook deploy-prod.yml'
                    } else {
                        bat 'ansible-playbook deploy-prod.yml'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            emailext subject: 'Build Success',
                     body: 'The build was successful',
                     attachLog: true,
                     to: 'mahsanaj323@gmail.com'
        }
        failure {
            echo 'Pipeline failed!'
            emailext subject: 'Build Failure',
                     body: 'The build failed. Please check the logs.',
                     attachLog: true,
                     to: 'mahsanaj323@gmail.com'
        }
    }
}
