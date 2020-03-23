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
                bat 'mvn build'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
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
