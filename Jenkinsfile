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
                ansiblePlaybook credentialsId: 'e6b451b2-986d-4b70-94a5-63cb8bc3b9f8', disableHostKeyChecking: true, installation: 'myapp', inventory: 'inventory', playbook: 'playbook_13.yaml',vaultCredentialsId: '9c283514-5fac-4462-949b-1b19c0dda46e'
            }
        }

        stage('Send HTTP request'){
            steps{
                httpRequest ignoreSslErrors: true, responseHandle: 'NONE', url: 'http://192.168.56.140/', validResponseCodes: '200', wrapAsMultipart: false
            }
        }
    }
}
