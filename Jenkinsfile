pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fakrul/nac_ansible'
            }
        }
        stage('basic system configuration - dns, ntp, snmp') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'main2.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
        stage('configure routing') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'main.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
    }
}
