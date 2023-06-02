pipeline {
    agent any

    stages {
        stage('Run') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'sandeep-github-app',
                                          usernameVariable: 'GITHUB_APP',
                                          passwordVariable: 'GITHUB_ACCESS_TOKEN')]) {
                sh "curl --write-out '%{http_code}' --silent --output /dev/null https://google.com"
                sh "/bin/bash health-check.sh"
                }
            }
        }
    }
}
