pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
       timeout(120) {
          waitUntil() {
              sh 'kubectl get deploy udacity${BUILD_ID} -o json | jq \'.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status\' | tr -d \'"\''
          }
        }
      }
    }
  }
}
