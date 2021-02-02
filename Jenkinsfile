pipeline {
  agent {
    docker {
      image 'node'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install --registry=https://registry.npm.taobao.org'
      }
    }

    stage('test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'sh \'./jenkins/scripts/test.sh\''
      }
    }

    stage('dliver') {
      steps {
        sh 'sh \'./jenkins/scripts/deliver.sh\''
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh 'sh \'./jenkins/scripts/kill.sh\''
      }
    }

  }
}