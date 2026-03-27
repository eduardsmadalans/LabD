pipeline {
    agent any 
    stages {
        stage('install-pip-deps') { 
            steps {
                echo 'Installing dependencies'
				git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
				powershell 'ls'
				powershell '''
				python3 -m venv venv
				.\\venv\\bin\\Activate.ps1
				pip install -r requirements.txt'''
            }
        }
        stage('deploy-to-dev') { 
            steps {
                echo 'Deploying to dev'
				script {
					deploy("DEV",7001)
				}
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

def deploy(String env, int port){
	git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
	bat '''npm install -g pm2 
	    pm2 delete greetings-app-${env} & EXIT /B 0
	    pm2 start -n greetings-app-${env} app.py -- -- ${port}'''
	
}



