pipline {
        agent any
            tools {
                maven "MY_MAVEN"
        }
        stages {
                stage('Build') {
                        steps { 
                                sh 'mvn clean'
                        }
                }
                stage('Test') {
                        steps { 
                                sh 'mvn test'
                        }
                }
                stage('Compile') {
                        steps { 
                                sh 'mvn compile'
                        }
                }	
                stage('Package') {
                        steps { 
                                sh 'mvn package'
                        }
                }
		stage ('BuildDockerImage') {
			steps {
				sh 'docker build -t addressbook:latest .'
			}
		}
		stage ('Tag Docker Image ') {
			steps {
				script {
        				pom = readMavenPom file: 'pom.xml'
			}
			sh "docker tag addressbook:latest phanivch/addressbook:${pom.version}"
			}
		}
		stage ('Push Docker Image') {
			steps {
				withCredentials([usernamePassword(credentialsId: 'DOCKER_CREDS', passwordVariable: 'DOCKER_HUB_PWD', usernameVariable: 'DOCKER_HUB_USER')] {
                                sh 'docker login -u $DOCKER_HUB_USER -p $DOCKER_HUB_PWD'
                                }
				sh 'docker push phanivch/addressbook:pom.version'
			}
		}
        }
}
