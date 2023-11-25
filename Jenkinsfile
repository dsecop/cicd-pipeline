pipeline {
  agent any
  
  docker {
    image 'node:latest',
      args -p 3000:3000
  }
  
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
          sh './scripts/build.sh'
        }
      }
    }
  }
  environment {
    registry = 'secop/my-app'
  }
}
