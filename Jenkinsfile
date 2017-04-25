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
        sh '''echo "~~> Build is running on..."


hostname
uname -a'''
      }
    }
    stage('Commit') {
      steps {
        sh '''// Along with SHA-1 id of the commit, it will be useful to retrieve changeset associated with that commit
// This command results in output indicating several one of these and the affected files:
// Added (A), Copied (C), Deleted (D), Modified (M), Renamed (R)
commitChangeset = sh(returnStdout: true, script: 'git diff-tree --no-commit-id --name-status -r HEAD').trim()'''
      }
    }
  }
}