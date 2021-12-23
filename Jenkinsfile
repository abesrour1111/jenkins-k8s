pipeline {
  agent {
    kubernetes {
      // this label will be the prefix of the generated pod's name
      label 'master'
      yaml """
apiVersion: v1
kind: Pod
metadata:
  inheritFrom:
    component: ci
spec:
  containers:
    - name: python
      image: python:3.7
      command:
        - cat
      tty: true
"""
    }
  }

  stages {
    stage('Test python') {
      steps {
        container('python') {
          sh "pip install -r requirements.txt"
          sh "python test.py"
        }
      }
    }
  }

}
