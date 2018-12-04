pipeline {
  agent {
    docker {
      image 'python:2.7-slim'
      args '-p 5000:5000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'sh \'python --version\''
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input '<"Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}