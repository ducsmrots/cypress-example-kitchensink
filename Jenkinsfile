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
                sh 'nohup npm start &'
                sh 'npm run local:run'
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