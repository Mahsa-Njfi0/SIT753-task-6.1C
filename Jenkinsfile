post {
    success {
        echo 'Pipeline completed successfully!'
        emailext(
            subject: 'Pipeline Success',
            body: 'The pipeline has succeeded!',
            to: 'mahsanaj323@gmail.com',
            attachLog: true
        )
    }
    failure {
        echo 'Pipeline failed!'
        emailext(
            subject: 'Pipeline Failed',
            body: 'The pipeline has failed. Please check the logs.',
            to: 'mahsanaj323@gmail.com',
            attachLog: true
        )
    }
}
