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
                echo "Set: " + getCredentials()
                echo "Set (SAMPLE): " + getCredentials("key":"SAMPLE")
                echo "Set (TEST): " + getCredentials("key":"TEST")
                echo "Set (TEST-Default): " + getCredentials("key":"TEST", "default": "PAULA")
                
            }
            
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
