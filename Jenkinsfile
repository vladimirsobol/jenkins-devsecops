pipeline {
  agent {
    label 'host'
  }
  stages {
    stage('Echo step') {
      parallel {
        stage('Echo step') {
          steps {
            sh 'echo "Hello fellas"'
          }
        }

        stage('Build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
            sh 'ls -las .'
            deleteDir()
            sh 'ls -las .'
          }
        }

      }
    }

    stage('Run the tests') {
      agent {
        docker {
          image 'gradle:jdk11'
        }

      }
      steps {
        sh 'ci/unit-test-app.sh'
      }
    }

  }
}