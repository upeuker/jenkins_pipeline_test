@Library('my_logging') _

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script { 
                    log.info 'Start Build step'
                }
                echo 'Building..'
                script { 
                    log.warning 'Build step finished!'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
