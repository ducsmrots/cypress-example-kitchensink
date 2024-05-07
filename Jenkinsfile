pipeline {
    agent {
        label 'cypress'
    }
    stages {
        stage('Cypress') {
            steps {
                // Your build steps here
                container('cypress') {
                sh 'npm ci'
                sh 'npm run cy:verify'
                sh 'nohup npm run start &'
                sh 'sh "npm run e2e:record:parallel"'
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