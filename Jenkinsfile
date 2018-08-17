pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('dev003') {
      steps {
        input 'Deploy'
        sh './jenkins/scripts/deliver.sh'
        sh './jenkins/scripts/kill.sh'
      }
    }
    stage('int003') {
      steps {
        input 'Deploy'
        sh './jenkins/scripts/deliver.sh'
        sh './jenkins/scripts/kill.sh'
      }
    }
    stage('stg003') {
      steps {
        input 'Deploy'
        sh './jenkins/scripts/deliver.sh'
        sh './jenkins/scripts/kill.sh'
      }
    }
   stage('prod003') {
      steps {
        input 'Deploy'
        sh './jenkins/scripts/deliver.sh'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
  }
}
