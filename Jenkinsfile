pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      milestone()
      node {
        steps {
          sh 'npm install'
        }
      }
    }
    stage('Test') {
      node {
        steps {
          sh './jenkins/scripts/test.sh'
        }
      }
      milestone()
    }
    lock(resource: 'dev', inversePrecedence: true){
      node('dev') {
        stage('dev003') {
          steps {
            input 'Deploy'
            milestone()
          }
        }
      }
    }
  }
  environment {
    CI = 'true'
  }
}
