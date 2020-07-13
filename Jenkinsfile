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
			bat "./gradlew build'"
			bat "cd $ANDROID_HOME/tools/bin/sdkmanager --licenses"
            }
        }
       
    }
}
