pipeline {
    agent any

    stages {
        stage('Run') {
            steps {
                sh '/bin/bash health-check.sh'
            }
        }
    }
}
