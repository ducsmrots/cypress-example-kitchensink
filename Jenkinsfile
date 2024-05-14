pipeline {
    agent {
        label 'cypress'
    }
    stages {
        stage('Cypress') {
            steps {
                ansiColor('xterm') {
                // Your build steps here
                    container('cypress') {
                    sh 'npm install cypress-multi-reporters --save-dev'
                    sh 'nohup npm start &'
                    sh 'npm run local:run'
                    sh 'ls -lRt'
                    }
                }
            }
        }

    }
    post {
        always {
            container('cypress') {
                // Archive test artifacts
                archiveArtifacts artifacts: 'cypress/screenshots/**/*.*, cypress/videos/**/*.*', allowEmptyArchive: true

                // Clean up steps here, if necessary
                echo 'Pipeline completed.'
            }
        }
    }
}
