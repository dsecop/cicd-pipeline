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

    stage('Docker image build') {
      steps {
        script {
          def appImage = docker.build("${REGISTRY}:${env.BUILD_ID}")
        }

      }
    }

  }
  environment {
    REGISTRY = 'secop/my-app'
  }
}