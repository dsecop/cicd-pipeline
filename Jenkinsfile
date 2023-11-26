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
          '''chmod u+x scripts/build.sh ./scripts/build.sh'''
        }

      }
    }

    stage('Test') {
      steps {
        script {
          './scripts/test.sh'
        }

      }
    }

  }
  environment {
    REGISTRY = 'secop/my-app'
  }
}