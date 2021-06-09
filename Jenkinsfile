def USER
def PASSWORD
def TAG
def JENKINS_SERV
def SOURCE_GIT


environment{
	DOCKERHUB_CREDENTIALS = credentials('houssembenali-dockerhub')
}

pipeline {
    agent any
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
				sh "docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW"
                sh "docker push ${TAG}"
            }
        }
    }
}