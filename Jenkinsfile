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
                bat 'mvn compile'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/*.jar.*', onlyIfSuccessful: true
            junit 'build/reports/**/*.xml'
        }
    }
}
