pipeline {
    agent any
    stages {
        stage('Preparation') {
            steps {
						 sh "ls –ltr && pwd “
                          sh "unzip *.zip"
            }
        }
        stage('Build') {
            steps {
                  	sh "mvn -f demo-service-master/user-service clean package"
            }
        }
        stage(‘Test') {
            steps {
                   	sh "ls -ltr demo-service-master/user-service/target"
					sh "mvn -f demo-service-master/user-service test"
            }
        }
        stage('Artifact’) {
            steps {
                        sh "ls -ltr demo-service-master/user-service/target"
						archiveArtifacts artifacts: "**/*.jar", allowEmptyArchive: true
            }
        }
    }
}
