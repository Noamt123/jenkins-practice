pipeline {
    agent any
    stages {
      stage('Lint HTML') {
        steps {
          sh 'tidy -q -e *.html'
        }
      stage('Upload to AWS') {
        steps {
          withAWS(region:'us-east-1',credentials:'bear1') {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'notes.txt', bucket:'poopy-crap')
          }
        }
      }
    }
  }
}
