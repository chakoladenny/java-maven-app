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
        sh 'echo "Another Placeholder"'
        sh 'env'
        sh 'mvn --version'
        sh 'sh $WORKSPACE/buildjar.sh'
      }
    }

  }
}