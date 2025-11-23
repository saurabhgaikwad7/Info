@"
pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/saurabhgaikwad7/Info.git'
            }
        }

        stage('Deploy to IIS') {
            steps {
                bat '''
                robocopy . "C:\\inetpub\\wwwroot\\PortWebsite" /MIR
                echo Deployment Successful!
                '''
            }
        }
    }
}
"@ | Set-Content Jenkinsfile
