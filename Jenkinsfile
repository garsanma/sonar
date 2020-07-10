// Pipeline para proyectos Android
//
// V.1.0.0
//

def server_up = false

pipeline {
    agent none
    options {
        // No bajamos el repo automaticamente tras el pipeline ya que bajaremos otro
        //skipDefaultCheckout true
        // Para que por consola salga la hora
        timestamps()
    }
    stages {
        stage('Build') {
            steps {
				sh './gradlew build'
            }
        }
       
    }
}
