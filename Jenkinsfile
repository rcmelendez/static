pipeline {
     agent any
     stages {
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'bastion-roberto')
		  sh '''
		     echo "Validating file in S3 with cURL"'
		     curl -v https://s3-us-east-2.amazonaws.com/bastion-roberto/index.html
		  '''
                  }
              }
         }
     }
}
