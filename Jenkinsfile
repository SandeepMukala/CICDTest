pipeline {
  agent any
  stages {
    stage('Checkout & Build') {
      steps {
        echo 'Pipeline started'
        git 'https://github.com/SandeepMukala/CICDTest.git'
        sh 'mvn clean install package'
      }
    }
    stage('MUnit tests') {
      steps {
        sh 'mvn test'
        catchError() {
          echo 'MUnit Test failure'
        }

      }
    }
  }
}