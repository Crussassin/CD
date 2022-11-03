pipeline {
    agent any 
    stages {
        stage('Clone Git repo'){
            steps{
                git branch: 'main', credentialsId: 'github-ssh-key-git-crussassin', url: 'https://github.com/Crussassin/CD_test'
            }
        }

        stage('Send HTTP request'){
            steps{
                httpRequest ignoreSslErrors: true, responseHandle: 'NONE', url: 'http://192.168.56.140/', validResponseCodes: '200', wrapAsMultipart: false
            }
        }
    }
}
