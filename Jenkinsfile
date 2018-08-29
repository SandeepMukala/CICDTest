pipeline {
  agent any
  stages {
    stage('Checkout & Build') {
      steps {
        echo 'Pipeline started'
        git 'https://github.com/SandeepMukala/CICDTest.git'
        bat 'mvn clean install package'
      }
    }
    stage('MUnit tests') {
      steps {
        bat 'mvn test'
        catchError() {
          echo 'MUnit Test failure'
        }

      }
    }
  }
}