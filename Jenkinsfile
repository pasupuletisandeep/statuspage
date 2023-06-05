pipeline {
    agent any
    
    environment {
        Login = credentials('jenkins-token')
    }

    stages {
        stage('Run') {
            steps {
                sh "curl --write-out '%{http_code}' --silent --output /dev/null https://google.com"
                sh "git config --global credential.helper"
                sh "git config --system credential.helper"
                sh "git branch"
                sh "/bin/bash health-check.sh"
            }
        }
    }
}
