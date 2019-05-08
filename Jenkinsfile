pipeline {
    agent any
    options {
        //timeout(time: 1, unit: 'HOURS')
        timeout(time: 60, unit: 'SECONDS') 
    }
    stages {
        stage('Preparation') {
            steps {
                    sh "ls -ltr"
                    sh "pwd"
                    sh "unzip -tq *.zip"
            }
        }
        stage('Build') {
            steps {
                    
		   sh "mvn -f demo-service-master/user-service clean war:war"
            }
        }
	stage('Test') {
            steps {
                    sh "ls -ltr demo-service-master/user-service/target"
		    sh "mvn -f demo-service-master/user-service test"
            }
        }
	stage('Artifact') {
            steps {
                    sh "ls -ltr demo-service-master/user-service/target"
                    sh "rm -f *.zip"
		    archiveArtifacts artifacts: "**/*.war", allowEmptyArchive: true
		    echo "Done..."
            }
        }
    }
}
