pipeline {
  agent {
    docker {
      image 'maven:3.9.2-eclipse-temurin-17'
    }

  }
  stages {
    stage('Fluffy Build') {
      agent any
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