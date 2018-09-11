pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Pipeline triggered'
        sh 'mvn clean package'
      }
    }
    stage('MUnit Test') {
      steps {
        echo 'running munits'
        sh 'mvn test'
      }
    }
  }
}