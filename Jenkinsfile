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
		sh "./gradlew assembleDebug"
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
    }
}  
