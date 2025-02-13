pipeline {
  agent {
    node {
      label 'worker'
    }

  }
  stages {
    stage('Fluffy Build') {
      steps {
        sh 'whoami'
        sh 'sh $WORKSPACE/buildjar.sh'
      }
    }

  }
}