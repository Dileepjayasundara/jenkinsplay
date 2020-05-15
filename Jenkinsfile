pipeline {

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/Dileepjayasundara/jenkinsplay.git', branch:'master'
      }
    }

    stage('Approval') {
            // no agent, so executors are not used up when waiting for approvals
            agent none
            steps {
              input "Deploy to production? "
            }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "k8s-stg-config")
        }
      }
    }

  }

}