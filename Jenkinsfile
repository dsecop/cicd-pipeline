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
    stage('Application build') {
      steps {
        script {
          sh 'chmod u+x scripts/build.sh'
          sh './scripts/build.sh'
        }
      }
    }
    stage('Test') {
      steps {
        script {
          sh './scripts/test.sh'
        }
      }
    }
    stage('Image build') {
      steps {
        script {
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }
      }
    }
  }
  environment {
    registry = 'secop/my-app'
  }
}
