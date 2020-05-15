pipeline {

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/Dileepjayasundara/jenkinsplay.git', branch:'master'
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "k8s-stg-config")
        }
      }
    }

    stage('Test app') {
      steps {
        echo "TEST STAGE"
      }
    }
  
    stage('Approval') {
      steps {
        input "Deploy to production? "
      }
    }

  

    stage('Deploy app in Production') {
      steps {
        echo "Production Deployment"
      }
    }

  }

}