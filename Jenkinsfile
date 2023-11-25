pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        script {
          checkout scm
        }

      }
    }

    stage('Application Build') {
      steps {
        sh 'sh \'./scripts/build.sh\''
      }
    }

  }
  environment {
    registry = 'secop/my-app'
  }
}