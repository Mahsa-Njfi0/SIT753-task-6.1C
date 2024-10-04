pipeline { 
    agent any 
 
    environment { 
        EMAIL_RECIPIENTS = 'mahsanaj323@gmail.com'  
    } 
 
    stages { 
 
        stage('Build') { 
            steps { 
                echo 'Stage: Build' 
                echo 'Task: Build the code using Maven' 
                echo 'Tool: Maven' 
            } 
        } 
 
        stage('Unit and Integration Tests') { 
            steps { 
                echo 'Stage: Unit and Integration Tests' 
                echo 'Task: Run unit tests to ensure code functions as expected and run 
integration tests to ensure components work together.' 
                echo 'Tool: JUnit' 
            } 
        } 
 
        stage('Code Analysis') { 
            steps { 
                echo 'Stage: Code Analysis' 
                echo 'Task: Perform static code analysis to ensure code meets industry 
standards.' 
                echo 'Tool: SonarQube' 
            } 
        } 
 
        stage('Security Scan') { 
            steps { 
                echo 'Stage: Security Scan' 
                echo 'Task: Perform a security scan to identify vulnerabilities in the code.' 
                echo 'Tool: OWASP Dependency-Check' 
            } 
        } 
 
        stage('Deploy to Staging') { 
            steps { 
                echo 'Stage: Deploy to Staging' 
                echo 'Task: Deploy the application to a staging server.' 
                echo 'Tool: AWS CLI' 
            } 
        } 
 
        stage('Integration Tests on Staging') { 
            steps { 
                echo 'Stage: Integration Tests on Staging' 
                echo 'Task: Run integration tests on the staging environment.' 
                echo 'Tool: Custom Test Scripts' 
            } 
        } 
 
        stage('Deploy to Production') { 
            steps { 
                echo 'Stage: Deploy to Production' 
                echo 'Task: Deploy the application to a production server.' 
                echo 'Tool: AWS CLI' 
            } 
        } 
    } 
 
    post { 
        success { 
            echo 'Pipeline completed successfully.' 
            emailext( 
                to: env.EMAIL_RECIPIENTS, 
                subject: "SUCCESS: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}", 
                body: """Good news! The pipeline for ${env.JOB_NAME} #${env.BUILD_NUMBER} 
completed successfully. 
 
Check the attached log file for details.""", 
                mimeType: 'text/plain', 
                attachLog: true // This will attach the console log to the email 
            ) 
        } 
        failure { 
            echo 'Pipeline failed.' 
            emailext( 
                to: env.EMAIL_RECIPIENTS, 
                subject: "FAILURE: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}", 
                body: """Unfortunately, the pipeline for ${env.JOB_NAME} 
#${env.BUILD_NUMBER} failed. Please check the attached log file for more details.""", 
                mimeType: 'text/plain', 
                attachLog: true // This will attach the console log to the email 
            ) 
        } 
        always { 
            echo 'Pipeline completed.' 
        } 
    } 
} 
 
//test
