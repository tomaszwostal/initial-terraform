pipeline {
    options {
		buildDiscarder(logRotator(numToKeepStr: '5'))
        timestamps()
        timeout(time: 30, unit: 'MINUTES')
    }
    agent any

	stage('Say Hello') {
		steps {
			script {
				sh('echo \"Hello\"');
			}
		}
	}
}
