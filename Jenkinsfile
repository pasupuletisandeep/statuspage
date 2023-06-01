pipeline {
    agent none

    stages {
        stage('Run') {
            steps {
                sh '/bin/bash health-check.sh'
            }
        }
    }
}
