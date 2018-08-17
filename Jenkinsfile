pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      sh 'npm install'
    }

    milestone 1
    stage('dev003') {
      lock(resource: 'staging-server', inversePrecedence: true) {
            milestone 2
            node {
                echo 'Deploying'
            }
            input message: "Does dev003 look good?"
        }
    }
  }
  environment {
    CI = 'true'
  }
}
