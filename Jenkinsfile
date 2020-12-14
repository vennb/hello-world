node('s390x_cocoa') {
  try {

    stage 'Build'
    node('s390x_cocoa') {
        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
    }
  } catch(Exception e) {
    throw e
  }
}
