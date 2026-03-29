pipeline {
    agent any 
    stages {
        stage('install-pip-deps') { 
            steps {
                echo 'Installing dependencies'
				git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
				bat "dir"
				bat "python -m venv venv"
				bat ".\\venv\\Scripts\\python.exe -m pip install -r requirements.txt"
            }
        }
        stage('deploy-to-dev') { 
            steps {
                echo 'Deploying to dev'
				script {
					deploy("dev",7001)
				}
            }
        }
        stage('tests-on-dev') { 
            steps {
                echo 'testing on dev'
				script {
					test("dev")
				}
            }
        }
		stage('deploy-to-stg') { 
            steps {
                echo 'deploying to stage' 
				script {
					deploy("stg",7002)
				}
            }
        }
		stage('tests-on-stg') { 
            steps {
                echo 'testing on stage' 
				script {
					test("stg")
				}
            }
        }
		stage('deploy-to-preprod') { 
            steps {
                echo 'deploying to pre-production'
				script {
					deploy("preprod",7003)
				}
            }
        }
		stage('tests-on-preprod') { 
            steps {
                echo 'testing on pre-production' 
				script {
					test("preprod")
				}
            }
        }
		stage('deploy-to-prod') { 	
            steps {
                echo 'deploying to pre-production'
				script {
					deploy("prod",7004)
				}
            }
        }
		stage('tests-on-prod') { 
            steps {
                echo 'testing on production'
				script {
					test("prod")
				}
            }
        }
    }
}

def deploy(String env, int port){
	git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
	bat "dir"
	//bat "npm install pm2"
	bat ".\\node_modules\\.bin\\pm2 delete greetings-app-${env} & EXIT /B 0"
	bat ".\\node_modules\\.bin\\pm2 start -n greetings-app-${env} app.py --interpreter \".\\venv\\Scripts\\python.exe\"  -- -- ${port}"
		
}

def test(String env){ 
	git branch: 'main', poll: false, url: 'https://github.com/mtararujs/course-js-api-framework'
	bat "dir"
	bat "npm install"
	bat "npm run greetings greetings_${env}"

	
}




