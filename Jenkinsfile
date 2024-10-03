pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                error 'Simulating a failure to trigger email notification' // Intentionally failing the build
            }
        }
    }

    post {
        always {
            // Send email with log attachment
            emailext to: 'mahsanaj323@gmail.com',
                     subject: "Jenkins Pipeline Status: ${currentBuild.currentResult}",
                     body: """The Jenkins pipeline ${env.JOB_NAME} - ${env.BUILD_NUMBER} has finished with status: ${currentBuild.currentResult}.
                     Check the attached log for more details.""",
                     attachLog: true
        }
    }
}
