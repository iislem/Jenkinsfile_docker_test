pipeline {
    agent any
    options {
        buildDiscarder(logRotator(daysToKeepStr: '50', numToKeepStr: '5'))
        timestamps()
        //Abort the build if it's stuck after 30 minutes
        timeout(time: 30, unit: 'MINUTES')
    }
    
    stages {
        stage("Prune Docker volumes"){
            agent any
                    steps {
                        script {
                                sh "ssh docker@192.168.1.54 -t 'docker system prune -af --volumes'"
                        }
                    }                 
        	}
    }
}
