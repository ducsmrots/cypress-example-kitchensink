pipeline {
    agent {
        label 'cypress'
    }
    stages {
        stage('Cypress') {
            steps {
                // Your build steps here
                container('cypress') {
                sh 'npm install'
                sh 'npm start'
                sh 'npm run local:open'
                }
            }
        }

    }
    post {
        always {
            // Clean up steps here, if necessary
            echo 'Pipeline completed.'
        }
    }
}