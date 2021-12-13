@Library('my_logging') _

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script { 
                    logging.info 'Start Build step'
                }
                echo 'Building..'
                script { 
                    logging.warning 'Build step finished!'
                }
                echo "${currentBuild.result}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                msgToTeams()
                   echo "${currentBuild.result}"
            }
          
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                 echo "${currentBuild.result}"
            }
        }
    }
    post {
    	always {
    		msgToTeams('type':'warning')
    		script {
	        	sendToTeams {
    	    	    type = 'error'
        		}
    		}
    		 echo "${currentBuild.result}"
        }
    }
}
