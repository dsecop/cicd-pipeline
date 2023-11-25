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

    stage('Test') {
      steps {
        script {
          sh './scripts/test.sh'
        }

      }
    }

    stage('Build') {
      steps {
        script {
          def customImage = docker.build("${image_name}")
        }

      }
    }

  }
  environment {
    image_name = 'mybuildimage  '
  }
}
