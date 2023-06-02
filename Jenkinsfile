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
                sh """
                git config --global user.name 'Vijaye Raji'
                git config --global user.email 'vijaye@statsig.com'
                git add -A --force logs/
                git commit -am '[Automated] Update Health Check Logs'
                git push https://github.com/pasupuletisandeep/statuspage.git HEAD:main
                """
                }
            }
        }
    }
}
