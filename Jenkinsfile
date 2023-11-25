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
          './scripts/test.sh'
        }
      }
    }
    stage('Docker image build') {
      steps {
        script {
          def customImage = docker.build("${REGISTRY}:${env.BUILD_ID}")
        }
      }
    }
    stage('Docker image push') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        sh "docker push $REGISTRY:${env.BUILD_ID}"
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
  environment {
    REGISTRY = 'secop/my-app'
    DOCKERHUB_CREDENTIALS = credentials('dockerhub_id')
  }
}
