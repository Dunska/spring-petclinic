pipeline {
  agent any
  stages {
    stage('Build & Unit Tests') {
      steps {
        node(label: 'build') {
          withMaven(
        maven: 'M3') {

      // Run the maven build
      sh "mvn clean install"

    }
stash(name: 'binaries', includes: 'target/\\*.jar')
        }

      }
    }
    stage('Static-analysis') {
      steps {
        node(label: 'build') {
          sleep 5
        }

      }
    }
    stage('Test Browser') {
      steps {
        parallel(
          "Edge": {
            node(label: 'build') {
              sleep 5
            }


          },
          "Chrome": {
            node(label: 'build') {
              sleep 4
            }


          },
          "Firefox": {
            node(label: 'build') {
              sleep 2
            }


          }
        )
      }
    }
    stage('Staging') {
      steps {
        unstash 'binaries'
        sh('ls -l target')
      }
    }
    stage('Mise en Prod') {
      steps {
        input(message: 'On met en prod ?', ok: 'C\'est parti !')
      }
    }
    stage('Deploy') {
      steps {
        node(label: 'build') {
          sleep 5
        }

      }
    }
  }

}
