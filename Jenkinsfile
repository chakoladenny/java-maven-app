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
        sh '''mvn --version
sh $WORKSPACE/buildjar.sh'''
      }
    }

  }
}