pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World!"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
            
         }
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'3ce3431b-3a95-43ea-a16e-7a01fdd9a528') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jjo-static-jenkins-pipeline')
                  }
              }
         }
     }
}
 