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
        script {
          def workerSizeInput = input(
            id: 'workerSizeInput', message: 'Please select vCores for Deployment:?',
            parameters: [
              [
                $class: 'ChoiceParameterDefinition', choices: '0.1\n0.2\n1\n2\n4\n8\n16',
                name: 'SELECTED_WORKER_VERSION',
                description: 'Please select worker version'
              ]])
              vCoreInput = "${workerSizeInput}"
              echo "$vCoreInput"
              bat "echo $vCoreInput"
              bat 'echo %WORKSPACE%'
              bat 'echo deploying artifact to cloud hub'
              bat "anypoint-cli runtime-mgr cloudhub-application deploy --runtime 3.9.0 --workerSize $vCoreInput \"cli-cicd\" \"%WORKSPACE%/target/cicdtest-1.0.0-SNAPSHOT.zip\" --username=\"sandeep_m\" --password=\"Whishworks@2018\""
            }

          }
        }
      }
    }