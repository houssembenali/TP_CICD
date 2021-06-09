def USER
def PASSWORD
def TAG
def JENKINS_SERV
def SOURCE_GIT




pipeline {
    agent any
	
	environment{
		DOCKERHUB_CREDENTIALS = credentials('houssembenali-dockerhub')
	}
    stages {
         stage('Initialisation des variables') {
            steps{
                script{
                    USER="houssembenali"
                    PASSWORD="MOT_DE_PASSE"
                    TAG="houssembenali/tp-cicd-ib"
                    JENKINS_SERV="http://192.168.1.124:3000"
                    SOURCE_GIT="https://github.com/houssembenali/TP_CICD.git"
                }
            }                
        }
        stage('git') {
            steps {
                git branch: 'main', url: "${SOURCE_GIT}"
            }
        }
        stage('Docker Build Image') {
            steps {
				sh "curl -X POST https://discordapp.com/api/webhooks/852186286508343296/0sEwrHLSCYIHA4cPpw3dJhf8uHv5tVn9SZsgQJ58HeU0Q2ywZWZPLGdxjMTDzO3WLf-v
					 -H \"Content-Type: application/json\" 
					 -d \"{\"content\":\"tst\"}\""
                sh "docker build -f ./docker/webapp/Dockerfile -t ${TAG} ."
            }
        }
        stage('Docker run') {
            steps {
                sh "docker run --rm -d --name tp_cicd_container -p 3000:3000 ${TAG} "
            }
        }
         stage('Test Container and stop') {
            steps {
				script{
					sh 'sleep 3'
					try{ 
						sh "curl ${JENKINS_SERV}"
					} finally {
						sh 'sleep 1'
						sh 'docker stop tp_cicd_container'
					}
				}
			}
        }
        stage('push') {
            steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh "docker push ${TAG}"
            }
        }
    }
}