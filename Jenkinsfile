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
                ansiblePlaybook credentialsId: 'ssh-key-for-servers', disableHostKeyChecking: true, installation: 'myapp', inventory: 'inventory', playbook: 'playbook_13.yaml',vaultCredentialsId: 'pass'
            }
        }

        stage('Send HTTP request'){
            steps{
                httpRequest ignoreSslErrors: true, responseHandle: 'NONE', url: 'http://192.168.56.140/', validResponseCodes: '200', wrapAsMultipart: false
            }
        }
    }
}
