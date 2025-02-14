pipeline {
  agent {
    node {
      label 'docker_worker'
    }

  }
  stages {
    stage('Fluffy Build') {
      agent any
      steps {
        sh 'whoami'
        sh 'sh $WORKSPACE/buildjar.sh'
        stash(name: 'stash-1', includes: 'target/*.jar')
      }
    }

    stage('Fluffy Test') {
      parallel {
        stage('Fluffy Test') {
          steps {
            unstash 'stash-1'
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

    stage('Fluffy Archive') {
      parallel {
        stage('Fluffy Archive') {
          steps {
            archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
          }
        }

        stage('pstage2') {
          steps {
            sh '''sleep 8
echo "final parallel stage - $AUTHOR"'''
          }
        }

      }
    }

  }
  environment {
    AUTHOR = 'denny'
  }
}