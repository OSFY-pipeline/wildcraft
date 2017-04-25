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
    stage('Commit') {
      steps {
        sh '''commit = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()'''
        sh '''sha1id = commit.take(7)'''
        sh ''' echo "~~> Commit id, ${sha1id}" '''
      }
    }
  }
}
