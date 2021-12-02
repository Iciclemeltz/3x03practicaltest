pipeline {
	agent any
	stages {
		stage ('Checkout') {
			steps {
				git branch:'master', url: 'https://github.com/janessatng/3x03practicaltest'
			}
		}
		stage('Code Quality Check via SonarQube') {
			steps {
				script {
					def scannerHome = tool 'SonarQube';
					withSonarQubeEnv('SonarQube') {
					sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=9592366d07658fdfa0ce9585043fc73bc9687d64 -Dsonar.projectKey=OWASP -Dsonar.sources=."
					}
				}
			}
		}
	}
	post {
		always {
			recordIssues enabledForFailure: true, tool: sonarQube()
		}
	}
}
