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

  }
}