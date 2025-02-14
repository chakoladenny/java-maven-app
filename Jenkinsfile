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

    stage('Fluffy Test') {
      parallel {
        stage('Fluffy Test') {
          steps {
            sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            junit '**/surefire-reports/**/*.xml'
          }
        }

        stage('pstage1') {
          steps {
            sh '''sleep 5
echo "a parallel stage - $AUTHOR"'''
          }
        }

      }
    }

    stage('pstage2') {
      steps {
        sh '''sleep 8
echo "final parallel stage - $AUTHOR"'''
      }
    }

    stage('Manual input') {
      steps {
        input(message: 'Deploy?', ok: 'yes')
      }
    }

    stage('Fluffy archive') {
      steps {
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
      }
    }

  }
  environment {
    AUTHOR = 'denny'
  }
}