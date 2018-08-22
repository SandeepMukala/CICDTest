pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        git(url: 'http://github.com/SandeepMukala/CICDTest.git', poll: true)
      }
    }
  }
}