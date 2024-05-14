// pipeline {
//     agent {
//         label 'cypress'
//     }
//     stages {
//         stage('Cypress') {
//             steps {
//                 // Your build steps here
//                 container('cypress') {
//                   sh 'npm install cypress-multi-reporters --save-dev'
//                   sh 'nohup npm start &'
//                   sh 'npm run local:run'
//                   sh 'ls -lrt'
//                 }
//             }
//         }

//     }
//     post {
//         always {
//             // Clean up steps here, if necessary
//             echo 'Pipeline completed.'
//         }
//     }
// }

pipeline {
  agent {
    // this image provides everything needed to run Cypress
    docker {
      image 'cypress/base:20.9.0'
    }
  }

  stages {
    stage('build and test') {
    //   environment {
    //     // we will be recording test results on Cypress Cloud
    //     // to record we need to set an environment variable
    //     // we can load the record key variable from credentials store
    //     // see https://jenkins.io/doc/book/using/using-credentials/
    //     CYPRESS_RECORD_KEY = credentials('cypress-example-kitchensink-record-key')
    //   }

      steps {
        sh 'npm ci'
        sh "npm run test:ci:record"
      }
    }
  }
}