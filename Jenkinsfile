pipeline {
  agent { label 'Built-In Node'}
  options {
    skipDefaultCheckout(true)
  }
  stages{
    stage('clean workspace') {
      steps {
        cleanWs()
      }
    }
    stage('checkout') {
      steps {
        checkout scm
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
