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
          sh 'npm install'
        }
      }
    }
  }
  environment {
    registry = 'secop/my-app'
  }
}
