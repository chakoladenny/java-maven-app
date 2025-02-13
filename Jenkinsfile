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
        sh 'env | grep -i maven'
        sh 'mvn --version'
        sh 'sh $WORKSPACE/buildjar.sh'
      }
    }

  }
  environment {
    MAVEN_HOME = '/root/jenkins_worker/maven'
  }
}