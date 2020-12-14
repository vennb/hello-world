 @Library('cocoa-jenkins-shared-library')_

node('s390x_cocoa') {
  try {

    stage 'Build'
    node('s390x_cocoa') {
        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
        sh 'hostnamectl'
     
        uploadEvidence artifactoryUsername: 'user',
               artifactoryPassword: 'password',
               namespace: 'ci',
               name: 'my-evidence',
               type: 'com.ibm.unit_test',
               typeVersion: '1.0',
               result: 'success',
               backend: 'cos',
               pipelineRunId: '123',
               pipelineId: 'XYZ',
    	          toolchainCrn: 'CRN',
               pipelineRunUrl: 'http://my-pipeline.ibm.com',
               cosApiKey: 'apikey',
               cosBucketName: 'my-bucket',
    	          cosEndpoint: 'cos-endpoint'
    }
  } catch(Exception e) {
    throw e
  }
}
