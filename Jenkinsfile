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
        script {
          sh 'npm install' sh './scripts/build.sh'
        }

      }
    }

  }
  environment {
    registry = 'secop/my-app'
  }
}