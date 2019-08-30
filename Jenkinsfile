pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
            sh '''
                echo READY=$(kubectl get deploy udacity97 -o json | jq '.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status' | tr -d '"')

            while [[ "$READY" != "True" ]]; do
                echo READY=$(kubectl get deploy $DEPLOYMENTNAME -o json | jq '.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status' | tr -d '"')
                sleep 5
            done

              '''

      }
    }
  }
}
