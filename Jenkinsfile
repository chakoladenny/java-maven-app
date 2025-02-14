pipeline {
  agent none
  stages {
    stage('Fluffy Build') {
      parallel {
        stage('Fluffy Build') {
          agent {
            node {
              label 'jenkins_worker'
            }

          }
          steps {
            sh 'whoami'
            sh 'sh $WORKSPACE/buildjar.sh'
            stash(name: 'java17', includes: 'target/**')
          }
        }

        stage('fluffy build 2') {
          agent {
            node {
              label 'docker_worker'
            }

          }
          steps {
            sh 'whoami'
            sh 'sh $WORKSPACE/buildjar.sh'
            stash(name: 'java11', includes: 'target/**')
          }
        }

      }
    }

    stage('Fluffy Test - FE') {
      parallel {
        stage('Fluffy Test - FE') {
          agent {
            node {
              label 'jenkins_worker'
            }

          }
          steps {
            unstash 'java17'
            sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            junit '**/surefire-reports/**/*.xml'
          }
        }

        stage('Fluffy Test - BE') {
          agent {
            node {
              label 'jenkins_worker'
            }

          }
          steps {
            unstash 'java17'
            sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            junit '**/surefire-reports/**/*.xml'
          }
        }

        stage('fluffy test 2 - FE') {
          agent {
            node {
              label 'docker_worker'
            }

          }
          steps {
            unstash 'java11'
            sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            junit '**/surefire-reports/**/*.xml'
          }
        }

        stage('fluffy test 2 - BE') {
          agent {
            node {
              label 'docker_worker'
            }

          }
          steps {
            unstash 'java11'
            sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            junit '**/surefire-reports/**/*.xml'
          }
        }

      }
    }

    stage('Manual input') {
      parallel {
        stage('Manual input') {
          steps {
            input(message: 'Deploy?', ok: 'yes')
          }
        }

        stage('manual inout 2') {
          steps {
            input(message: 'Deploy to docker', ok: 'yes')
          }
        }

      }
    }

    stage('Fluffy archive') {
      parallel {
        stage('Fluffy archive') {
          agent {
            node {
              label 'jenkins_worker'
            }

          }
          steps {
            archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
          }
        }

        stage('fluffy archiv 2') {
          agent {
            node {
              label 'docker_worker'
            }

          }
          steps {
            archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
          }
        }

      }
    }

  }
  environment {
    AUTHOR = 'denny'
  }
}