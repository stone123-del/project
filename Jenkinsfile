pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/stone123-del/project.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker push ilovesnows/portal:red
        '''
      }
    }
    stage('deploy and service') {
      steps {
        sh '''
        ansible-playbook /var/lib/jenkins/node.yml
        ansible-playbook /var/lib/jenkins/master.yml
        '''
      }
    }
  }
}
