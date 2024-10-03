pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Add your build steps here...
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test steps here...
            }
        }
    }

    post {
        always {
            emailext attachmentsPattern: '**/*.log', 
                     body: '''The build has finished with status: ${currentBuild.currentResult}. Please check the attached logs for more details.''', 
                     subject: 'Build Status: ${currentBuild.currentResult}', 
                     to: 'mahsanaj323@gmail.com'
        }
    }
}
