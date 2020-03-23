pipeline {
    agent any
    stages {
		
		stage("Scm clone"){
			steps{
				git 'https://github.com/Ramfunc/simpleboot'
			}
		}
		
        stage('Build') {
            steps {
                bash 'mvn build'
            }
        }
        stage('Test') {
            steps {
                bash 'mvn test'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
    }
}
