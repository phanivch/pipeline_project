pipeline {
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
                stage('compile') {
                        steps { 
                                sh 'mvn compile'
                        }
}
                stage('package') {
                        steps { 
                                sh 'mvn package'
                        }
                }
        }
}
