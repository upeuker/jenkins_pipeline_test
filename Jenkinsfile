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
                echo "Get: " + getCredentials()
                echo "Get (SAMPLE): " + getCredentials("key":"SAMPLE")
                echo "Get (TEST): " + getCredentials("key":"TEST")
                echo "Get (TEST-Default): " + getCredentials("key":"TEST", "default": "PAULA")
                
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
