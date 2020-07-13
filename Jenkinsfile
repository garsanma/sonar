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
       stage('Firma') {
	    steps {
		bat 'apksigner sign --ks C:\Proyectos\Cajamar\key\my-release-key.jks --ks-pass pass:changeit --ks-key-alias my-alias --key-pass pass:insa_2020 http://localhost:8080/job/Android-pipeline/27/artifact/app/build/outputs/apk/release/app-release-unsigned.apk
	    }
	}
    }
}
