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
        commit = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
        sha1id = commit.take(7)
      }
    }
  }
}
