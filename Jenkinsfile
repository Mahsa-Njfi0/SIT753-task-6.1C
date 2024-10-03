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
        failure {
            // Minimal emailext configuration
            emailext(
                to: 'mahsanaj323@gmail.com', // Your email
                subject: "Jenkins Pipeline Failed",
                body: "The Jenkins pipeline has failed. Please check the build logs for details."
            )
        }
    }
}
