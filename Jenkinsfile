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
        def workerSizeInput = input(
        id: 'workerSizeInput', message: 'Please select vCores for Deployment:?', 
        parameters: [
				[
					$class: 'ChoiceParameterDefinition', choices: '0.1\n0.2\n1\n2\n4\n8\n16', 
					name: 'SELECTED_WORKER_VERSION',
					description: 'Please select worker version'
				]])
    	vCoreInput = "${workerSizeInput}"
        echo 'deploying artifact to Cloud Hub'
        bat 'anypoint-cli runtime-mgr cloudhub-application deploy --runtime 3.9.0 --workerSize ${vCoreInput} "cli-cicd" "${workspace}/cli-cicd-test/target/cicdtest-1.0.0-SNAPSHOT.zip" --username="sandeep_m" --password="Whishworks@2018"'
      }
    }
  }
}
