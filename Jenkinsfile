pipeline {
    agent any

    stages {
        stage ('verify branch') {
            steps {
				echo "$GIT_BRANCH"
			}
		}
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fakrul/nac_ansible'
            }
        }
        stage('basic system configuration - dns, ntp, snmp') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'main-commonconfig.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
        stage('configure interfaces') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'main-interface.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
        stage('configure routing') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'main-routing.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
        stage('save configuration') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'main-saveconfig.yml', vaultCredentialsId: '5bc99d67-f650-44ce-bcc2-1aa00858124f'
            }
        }
    }
}
