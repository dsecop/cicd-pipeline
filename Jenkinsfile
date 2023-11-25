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
          sh 'chmod u+x scripts/build.sh'
          sh './scripts/build.sh'
        }
      }
    }
    stage('test') {
      steps {
        script {
          sh './scripts/test.sh'
        }
      }
    }
  }
  environment {
    registry = 'secop/my-app'
  }
}
