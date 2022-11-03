pipeline {
    agent any 
    stages {
        stage('Clone Git repo'){
            steps{
                git branch: 'main', credentialsId: 'github-ssh-key-git-crussassin', url: 'https://github.com/Crussassin/CD_test'
            }
        }
        stage('playbook'){
            steps{
                
                ansiblePlaybook credentialsId: '8fee0108-b311-40bd-9bc4-6528ab2dbde1', disableHostKeyChecking: true, installation: 'myapp', inventory: 'inventory', playbook: 'playbook_13.yaml',vaultCredentialsId: '9c283514-5fac-4462-949b-1b19c0dda46e'
            }
        }

        stage('Send HTTP request'){
            steps{
                httpRequest ignoreSslErrors: true, responseHandle: 'NONE', url: 'http://192.168.56.140/', validResponseCodes: '200', wrapAsMultipart: false
            }
        }
    }
}
