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

  }
  environment {
    registry = 'secop/my-app'
  }
}