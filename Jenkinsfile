pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Simulate a failure in the build step to trigger email notification
                error 'Simulating a build failure to test emailext'
            }
        }
    }

    post {
        failure {
            emailext(
                subject: "Pipeline Failure",
                body: "The pipeline has failed. Please check the Jenkins logs for details.",
                to: 'mahsanaj323@gmail.com'
            )
        }
    }
}
