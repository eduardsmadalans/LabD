pipeline {
    agent any 
    stages {
        stage('install-pip-deps') { 
            steps {
                echo 'Installing dependencies'
            }
        }
        stage('deploy-to-dev') { 
            steps {
                echo 'Deploying to dev'
            }
        }
        stage('tests-on-dev') { 
            steps {
                echo 'testing on dev' 
            }
        }
		stage('deploy-to-stg') { 
            steps {
                echo 'deploying to stage' 
            }
        }
		stage('tests-on-stg') { 
            steps {
                echo 'testing on stage' 
            }
        }
		stage('deploy-to-preprod') { 
            steps {
                echo 'deploying to pre-production'
            }
        }
		stage('tests-on-preprod') { 
            steps {
                echo 'testing on pre-production' 
            }
        }
		stage('deploy-to-prod') { 
            steps {
                echo 'deploying to pre-production'
            }
        }
		stage('tests-on-prod') { 
            steps {
                echo 'testing on production'
            }
        }
    }
}
