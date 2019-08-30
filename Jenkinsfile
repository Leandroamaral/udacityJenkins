pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        timeout(time: 120) {
          waitUntil() {
            sh '''
              echo READY=$(kubectl get deploy udacity97 -o json | jq \'.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status\' | tr -d \'"\')'
              if [ "$READY" != "True" ] then READY=False fi
              '''
            return $READY
          }

        }

      }
    }
  }
}
