pipeline {
  agent {
    node {
      label 'worker'
    }

  }
  stages {
    stage('Fluffy Build') {
      steps {
        sh 'echo $WORKSPACE'
        sh 'sh $WORKSPACE/buildjar.sh'
      }
    }

    stage('Fluffy Test') {
      steps {
        sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
      }
    }

    stage('Fluffy Deploy') {
      steps {
        sleep 5
        echo 'Deployed'
      }
    }

  }
  environment {
    LAB = 'dummy-lab'
  }
}