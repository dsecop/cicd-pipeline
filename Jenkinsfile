pipeline {
  agent any
  stages {
    // stage('Git checkout') {
    //   steps {
    //     script {
    //       checkout scm
    //     }
    //   }
    // }
    // stage('Application build') {
    //   steps {
    //     script {
    //       sh 'chmod u+x scripts/build.sh'
    //       sh './scripts/build.sh'
    //     }
    //   }
    // }
    // stage('Test') {
    //   steps {
    //     script {
    //       sh './scripts/test.sh'
    //     }
    //   }
    // }
    // stage('Image build') {
    //   steps {
    //     script {
    //       def customImage = docker.build("${REGISTRY}:${env.BUILD_ID}")
    //     }
    //   }
    // }
    stage('Docker login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
  }
  environment {
    REGISTRY = 'secop/my-app'
    DOCKERHUB_CREDENTIALS = credentials('dockerhub_id')
  }
}
