 @Library('cocoa-jenkins-shared-library')_

node('master') {
  try {
    node('master') {
        echo "Running ${env.BUILD_ID} from ${env.JENKINS_URL}"
        sh 'hostnamectl'
     
        uploadArtifact artifactoryUsername: 'vennb@uk.ibm.com',
               artifactoryPassword: 'AKCp5fTQuZgypC2TMjELowTamUPT7D2KMN4hEyQFGZ6MScXAAR9tLGoWP4mKLrnPJi2GdbjkA',
               namespace: 'ci',
               filePath: '${WORKSPACE}',
               backend: 'cos',
               pipelineRunId: '123',
               cosApiKey: '4wvMBGvSLZrreVMmJYHlej0nYY5xPiq8VJ5_iK9fvDgp',
               cosBucketName: 'cloud-object-storage-qh-cos-standard-itj',
               cosEndpoint: 's3.eu-gb.cloud-object-storage.appdomain.cloud'
    }
  } catch(Exception e) {
    throw e
  }
}
