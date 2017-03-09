pipeline {
  agent none
  stages {
    stage('Build & Unit Tests') {
      steps {
        node(label: 'build') {
          sleep 5
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
        node(label: 'build') {
          sleep 5
        }

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
