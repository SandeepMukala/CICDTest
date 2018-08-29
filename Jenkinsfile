pipeline {
  agent any
  stages {
    stage('Checkout & Build') {
      steps {
        echo 'Pipeline started'
        git 'https://github.com/SandeepMukala/CICDTest.git'
        bat 'mvn clean install package -DskipTests=true'
      }
    }
    stage('MUnit tests') {
      steps {
        bat 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        input 'Select the size of vCore'
      }
    }
  }
}