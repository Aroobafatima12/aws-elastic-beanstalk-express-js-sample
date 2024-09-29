  pipeline {
      agent {
          docker {
              image 'node:16'
              label ''
          }
      }

      stages {
          stage('Test Docker') {
              steps {
                  sh 'docker --version'
              }
          }

      stages {
          stage('Iinstall Dependencies') {
              steps {
                  sh 'npm install -g synk'
                  sh 'synk test'
               }
           }

           stage('Build') {
               steps {
                   sh 'npm run build'
               }
           }

           stage('Test') {
               steps {
                   sh 'npm test'
               }
           }
       }
 
       post {
           failure {
               mail to: 'you@example.com',
                    subject: "Build failed in Jenkins: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                    body: "Build failed! Check Jenkins for details"
           }
       }
  }
