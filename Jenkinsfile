@Library('cocoa-jenkins-shared-library')_

node('master') {
  try {
     
        stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
          checkout scm
        }
        
        stage('Build image') {
             dir("${env.WORKSPACE}/arm64v8/hello-world"){
                 docker.build("s390x/hello-world")
             }
         }
     
       stage('Upload to COS'){
        withCredentials([string(credentialsId: 'ibm-cos-apikey', variable: 'COS_APIKEY'),
                        usernamePassword(credentialsId: 'vennb-artifactory-api', passwordVariable: 'ARTIFACTORY_PASSWORD', usernameVariable: 'ARTIFACTORY_USER')]) {
           
         uploadEvidence artifactoryUsername: '$ARTIFACTORY_USER',
               artifactoryPassword: '$ARTIFACTORY_PASSWORD',
               namespace: 'ci',
               name: 'bv-evidence',
               type: 'com.ibm.unit_test',
               typeVersion: '1.0',
               result: 'success',
               backend: 'cos',
               pipelineRunId: "$BUILD_NUMBER",
               pipelineId: "$JOB_NAME",
    	         toolchainCrn: 's3.eu-gb.cloud-object-storage.appdomain.cloud',
               pipelineRunUrl: "$BUILD_URL",
               cosApiKey: "$COS_APIKEY",
               cosBucketName: 'cloud-object-storage-qh-cos-standard-itj',
               cosEndpoint: 's3.eu-gb.cloud-object-storage.appdomain.cloud'
         
         uploadArtifact artifactoryUsername: '$ARTIFACTORY_USER',
                artifactoryPassword: '$ARTIFACTORY_PASSWORD',
                namespace: 'ci',
                filePath: '$JENKINS_HOME/jobs/${JOB_NAME}/builds/$BUILD_NUMBER/log',
                backend: 'cos',
                pipelineRunId: "$BUILD_NUMBER",
                cosApiKey: "$COS_APIKEY",
                cosBucketName: 'cloud-object-storage-qh-cos-standard-itj',
                cosEndpoint: 's3.eu-gb.cloud-object-storage.appdomain.cloud'
        }
    }
  } catch(Exception e) {
    throw e
  }
}
