pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fakrul/nac_ansible'
            }
        }
        stage('configure nameserver') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'set_nameserver.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
        stage('configure ntp') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'set_ntp.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
        stage('configure snmp') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'set_snmp.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
    }
}
