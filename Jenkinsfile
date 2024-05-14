// 

pipeline {
    agent {
        label 'cypress'
    }
    stages {
        stage('Cypress') {
            steps {
                container('cypress') {
                    script {
                        // Install cypress-multi-reporters and strip-ansi packages
                        sh 'npm install cypress-multi-reporters --save-dev'
                        sh 'npm install strip-ansi --save-dev'

                        // Start the server in the background
                        sh 'nohup npm start &'

                        // Run Cypress tests and save the output to a file
                        sh 'npm run local:run > cypress-output.log'

                        // Create the Node.js script to clean the output
                        writeFile file: 'clean-output.js', text: """
                            const fs = require('fs');
                            const stripAnsi = require('strip-ansi');

                            const input = fs.readFileSync('cypress-output.log', 'utf8');
                            const output = stripAnsi(input);

                            fs.writeFileSync('cleaned-output.log', output);
                        """

                        // Run the Node.js script to clean the output
                        sh 'node clean-output.js'

                        // Read and print the cleaned output
                        def cleanOutput = readFile('cleaned-output.log').trim()
                        echo cleanOutput

                        // Optionally, list the directory contents to check files
                        sh 'ls -lrt'
                    }
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
