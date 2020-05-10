def k8s

pipeline {
  agent any

  stages {
    stage ('Delete Resources') {
      steps {
        sh 'rm k8s-deploy-go-artifact.yaml'
      }
    }
    stage ('Start Environment') {
      steps {
        sh 'docker start c531 && kind export kubeconfig'
      }
    }
    stage ('Copy YAML') {
      steps {
        sh 'cp k8s-deploy-go-artifact.yaml .'
      }
    }
    stage ('Deploy Image') {
      steps {
        sh 'kubectl apply -f ./k8s-deploy-go-artifact.yaml'
      }
    }
    stage ('Test Deployment') {
      steps {
        sh 'curl http://10.10.50.4:9090'
      }
    }
  }
}
