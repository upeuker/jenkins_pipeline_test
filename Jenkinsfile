@Library('my_logging') _

pipeline {
    agent any

	environment {
	    AAA = 'true'
        BBB    = 'sqlite'
	}
	
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
            getCredentials()
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
            post {
                failure {
                    msgToTeams("subject": "Fehler beim Test", "attachLog": "true") 
                }

            }

          
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                msgToTeams("subject": "Deployed") 
            }
        }
    }
    post {
    	always {
    		msgToTeams()
        }
    }
}
