pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'kubectl get deploy udacity93 -o json | jq \'.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status\' | tr -d \'"\''
      }
    }
  }
}