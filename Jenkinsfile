pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Simulate success or failure
                // Uncomment the next line to test failure case
                // error 'Failing the build to test email'
            }
        }
    }

    post {
        always {
            emailext (
                to: 'mahsanaj323@gmail.com',
                subject: "Build Status: ${currentBuild.currentResult}",
                body: """The Jenkins build ${env.JOB_NAME} - ${env.BUILD_NUMBER} has completed with status: ${currentBuild.currentResult}.
                         Check the attached log for more details.""",
                attachLog: true
            )
        }
    }
}
