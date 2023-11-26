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
    REGISTRY = 'secop/my-app'
  }
}