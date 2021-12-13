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
                echo "Buildstatus: '${currentBuild.result}'"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
              //  msgToTeams()
                   echo "Buildstatus: '${currentBuild.result}'"
            }
          
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                 echo "Buildstatus: '${currentBuild.result}'"
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
    		 echo "Buildstatus '${currentBuild.result}'"
        }
    }
}
