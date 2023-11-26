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
          '''
          chmod u+x scripts/build.sh 
          ./scripts/build.sh
          '''
        }
      }
    }
    stage('Tests') {
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
    stage('Docker image push') {
      steps {
        script {
          docker.withRegistry('', 'dockerhub_id') {
            docker.image("${REGISTRY}:${env.BUILD_ID}").push('latest')
            docker.image("${REGISTRY}:${env.BUILD_ID}").push("${env.BUILD_ID}")
          }
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
    }
  }
