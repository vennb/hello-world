@Library('cocoa-jenkins-shared-library')

node('s390x_cocoa') {
  try {

    stage 'Build'
    node('s390x_cocoa') {
        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
        sh 'hostnamectl'
    }
  } catch(Exception e) {
    throw e
  }
}
