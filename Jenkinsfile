pipeline {
    agent {label 'Jenkins-WS'}
    
    environment{                           
        SSH_CRED = credentials('SSH_CREDS')
    }
    stages{
        stage('Performing Ansible Dry Run'){
            sh "ansible-playbook -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW} -e COMPONENT=mongodb -e ENV=qa robo-dryrun.yaml"
        }
    }
}