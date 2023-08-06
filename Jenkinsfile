pipeline {

  agent none
  // None: khia báo agent khia chạy từng stage
  // khai báo ở đây thì chạy chung nguyên stage

  environment{}

  stages{
    stage("TEST"){
      agent{
        docker{
          image 'python:3.8-slim-buster'
          args '-u 0:0 -v /tmp:/root/.cache'
        }
      }
      steps {
        sh "pip install poetry"
        sh "poetry install"
        sh "poetry run pytest"
      }
    }
  }

  post{
    success {
      echo "SUCCESSFUL"
    }
    failure {
      echo "FAILED"
    }
  }

}