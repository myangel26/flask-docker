pipeline {

  agent {
    kubernetes{
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          serviceAccountName: jenkins-admin
          containers:
            - name: python
              image: docker
              securityContext:
                runAsUser: 0
                runAsGroup: 0
      '''
    }
  }
  // None: khia báo agent khia chạy từng stage
  // khai báo ở đây thì chạy chung nguyên stage

  // environment{}

  stages{
    stage("TEST"){
      steps {
        container('python') {
          // sh "pip install poetry" 
          // sh "poetry install"
          // sh "poetry run pytest"
          sh "docker"
        }
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