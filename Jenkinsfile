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
          }
        }

      }
    }

    stage('Archive the artifacts') {
      steps {
        archiveArtifacts(artifacts: '*', allowEmptyArchive: true)
      }
    }

  }
}