pipeline {
	agent any
	stages {
		stage('Pre-build') {
			agent any
			steps {
				sh 'echo "Install pre-reqs here!"'
			}
		}
		stage('Build') {
			failFast true
			parallel {
				stage('Build-1') {
					agent any
					steps {
						sh 'echo "I can go with npm i, npm build, stuff here"'
					}
					post {
						success {
							sh 'echo "Stashed!"'
						}
					}
				}
				stage('Build-2') {
					agent any
					steps {
						sh 'echo "Second build in parallel"'
					}
				}
			}
		}
		stage('Test') {
			steps {
				sh 'echo "AGAI?N!"'
			}
		}
		stage('Confirm?') {
			steps {
				timeout(time: 3, unit: 'HOURS') {
					input(message: 'Ok to deploy?', ok: 'YES')
				}
			}
		}
		stage('Deploy') {
			steps {
				sh 'echo "Deploying!"'
			}
		}
	}
}
