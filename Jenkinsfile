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
                sh """
                git add -A --force logs/
                git commit -am '[Automated] Update Health Check Logs'
                git push https://$Login@github.com/pasupuletisandeep/statuspage.git HEAD:main
                """
            }
        }
    }
}
