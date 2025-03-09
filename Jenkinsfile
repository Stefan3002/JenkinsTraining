pipeline {
	agent none
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
							stash(name: 'my-app', includes: 'app_path')
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
				timeout(time: 3, unit: 'HOUR')
				input(message: 'Ok to deploy?', ok: 'YES')
			}
		}
		stage('Deploy') {
			steps {

			}
		}
	}
}
