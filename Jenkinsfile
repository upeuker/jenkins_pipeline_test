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
            post {
                failure {
                    msgToTeams("subject": "Fehler beim Test", "attachLog": "true") 
                }

            }

          
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                echo "Buildstatus: '${currentBuild.result}'"
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
