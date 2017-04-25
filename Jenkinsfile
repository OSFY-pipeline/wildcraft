pipeline {
  agent any
  stages {
    stage('Cleanup') {
      steps {
        deleteDir()
      }
    }
    stage('Sysinfo') {
      steps {
        sh '''
              echo "~~> Build is running on..."
              hostname
              uname -a
           '''
      }
    }
  }
}
