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
                git config --global user.name 'sandeep'
                git config --global user.email 'sandeep.vinny@gmail.com'
                git add -A --force logs/
                git commit -am '[Automated] Update Health Check Logs'
                git push https://sandeep:$jenkins-token@github.com/pasupuletisandeep/statuspage.git HEAD:main
                """
            }
        }
    }
}
