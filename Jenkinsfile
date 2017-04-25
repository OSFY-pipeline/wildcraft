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
        sh '''
        commit = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
        sha1id = commit.take(7)
        commitChangeset = sh(returnStdout: true, script: 'git diff-tree --no-commit-id --name-status -r HEAD').trim()
        println "~~> changeset that is part of commit id, ${sha1id}, is, ${commitChangeset}" 
        '''
      }
    }
  }
}
