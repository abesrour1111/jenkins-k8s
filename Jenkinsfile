pipeline {
  agent {

 kubernetes {
      // this label will be the prefix of the generated pod's name
      label 'jenkins/'
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
    stage('stage 1') {
      parallel {
        stage('stage 1') {
          steps {
            sh '''cut -d: -f1,3 /etc/passwd > /tmp/users
cut -d: -f1,3 /etc/passwd > /tmp/users'''
          }
        }

        stage('stage 1-2') {
          steps {
            sh 'cut -d: -f4 /etc/passwd |sort | uniq > /tmp/ids_groupes_prim'
          }
        }

        stage('stage 1-3') {
          steps {
            sh 'cut -d: -f4 /etc/passwd |sort | uniq > /tmp/ids_groupes_prim'
          }
        }

      }
    }

    stage('stage 2') {
      steps {
        sh 'diff /tmp/ids_groupes_prim /tmp/id_groupes > test'
        sh 'nombre=`wc -l test`
      }
    }

  stage ('test')
  {
    when {expression { x == 0 }
    steps {

echo "les fichiers sont identiques"
}

}
}
    post
    {
      failure {
      echo "les fichiers sont différents"
      }
      success
      {
       echo "les fichiers sont identiques "
      }
      always
      {
       echo "fin de l'exercice" 
      }
    }

  
}
