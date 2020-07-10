// Pipeline para proyectos Android
//
// V.1.0.0
//

def server_up = false

pipeline {
    agent any
  tools {
    gradle 'gradle-jenkins'
  }
    stages {
        stage('Build') {
            steps {
		sh './gradlew build'
            }
        }
       
    }
}
