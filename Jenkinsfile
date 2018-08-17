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
        milestone 1
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      lock(resource: 'staging-server', inversePrecedence: true) {
        milestone 2
        steps {
          sh './jenkins/scripts/deliver.sh'
          input 'Finished using the web site? (Click "Proceed" to continue)'
          sh './jenkins/scripts/kill.sh'
        }
      }
    }
  }
  environment {
    CI = 'true'
  }
}
