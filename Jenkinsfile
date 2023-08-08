pipeline {

  agent none
  // agent {
  //   kubernetes{
  //     yaml '''
  //       apiVersion: v1
  //       kind: Pod
  //       spec:
  //         serviceAccountName: jenkins-admin
  //         containers:
  //           - name: python
  //             image: python:3.8-slim-buster
  //             command:
  //             - cat
  //             tty: true
  //             securityContext:
  //               runAsUser: 0
  //               runAsGroup: 0
  //             volumeMounts:
  //             - mountPath: /root/.cache
  //               name: python-cache
  //         volumes:
  //           - name: python-cache
  //             hostPath:
  //               path: /tmp
  //     '''
  //   }
  // }
  // None: khia báo agent khia chạy từng stage
  // khai báo ở đây thì chạy chung nguyên stage

  // environment{}

  stages{
    stage("TEST"){
      agent {
          docker {
            image 'python:3.8-slim-buster'
            args '-u 0:0 -v /tmp:/root/.cache'
          }
      }
      steps {
        container('python') {
          sh "pip install poetry" 
          sh "poetry install"
          sh "poetry run pytest"
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