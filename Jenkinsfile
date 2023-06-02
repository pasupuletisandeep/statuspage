pipeline {
    agent any
    
    environment {
        Login = credentials('jenkins-token')
    }

    stages {
        stage('Run') {
            steps {
                sh "curl --write-out '%{http_code}' --silent --output /dev/null https://google.com"
                sh "/bin/bash health-check.sh"
            }
        }
    }
}
