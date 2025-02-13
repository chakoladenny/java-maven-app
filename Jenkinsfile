pipeline {
  agent {
    node {
      label 'worker'
    }

  }
  stages {
    stage('Fluffy Build') {
      steps {
        echo 'Placeholder'
        sh 'sh $WORKSPACE/buildjar.sh'
      }
    }

  }
}