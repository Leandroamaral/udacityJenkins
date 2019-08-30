pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        timeout(120) {
           waitUntil {
            def r = sh script: "kubectl get deploy udacity97 -o json | jq '.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status' | tr -d '"')"
            return r == 0
            

      }
    }
  }
}
