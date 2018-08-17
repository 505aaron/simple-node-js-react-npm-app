stage('build') {
  node {
    sh 'npm install'
  }
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
