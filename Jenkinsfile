// Pipeline para proyectos Android
//
// V.1.0.0
//

def server_up = false

pipeline {
	//agent any
    agent { label "sdk5" }
    stages {
        stage('Build') {
            steps {
		sh "./gradlew build"
            }
        }
	stage('Compile') {
	    steps {
            archiveArtifacts artifacts: '**/*.apk', fingerprint: true, onlyIfSuccessful: true            
	    }
	}
	
    }
}  
