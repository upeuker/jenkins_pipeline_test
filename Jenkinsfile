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
    		 echo "BODY: Check console output at ${BUILD_URL} to view the results"
    		 echo "SUBJ: Build state in Jenkins: ${JOB_BASE_NAME} - #${BUILD_NUMBER} ${currentBuild.result}"
    		 
    		 // mail body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', subject: 'Build state in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER ${currentBuild.result}', to: 'dev@upeuker.net'
    		 mail body: 'Check console output at $BUILD_URL to view the results.', subject: 'Build state in Jenkins: $JOB_NAME', to: 'dev@upeuker.net'
        }
    }
}
