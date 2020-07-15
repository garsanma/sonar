// Pipeline para proyectos Android
//
// V.1.0.0
//

def server_up = false

pipeline {
    agent { label "win" }
    stages {
        stage('Build') {
            steps {
		bat "./gradlew assembleDebug"
            }
        }
	stage('Compile') {
	    steps {
            archiveArtifacts artifacts: '**/*.apk', fingerprint: true, onlyIfSuccessful: true            
	    }
	}	
	stage ('sign apk') { 
	    steps{
	    signAndroidApks ( 
	    keyStoreId: "AndroidSign", 
	    keyAlias: "my-alias", 
	    apksToSign: "**/*-unsigned.apk" 
	    ) 
	    }
    	} 
	stage('Sonarqube') {
	    environment {
		scannerHome = tool 'SonarQubeScanner'
	    }
	    steps {
		withSonarQubeEnv('sonarqube') {
		    sh "${scannerHome}/bin/sonar-scanner"
		}
		timeout(time: 10, unit: 'MINUTES') {
		    waitForQualityGate abortPipeline: true
		}
    }
}
    }    
}
