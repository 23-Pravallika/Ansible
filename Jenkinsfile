pipeline {
    agent {label 'Jenkins-WS'}
    
    environment{                           
        SSH_CRED = credentials('SSH_CREDS')
    }
    stages{
        
        // stage('Performing Lint Check'){
        //     when {
        //         branch pattern: "feature-.*", comparator: "REGEXP"
        //     }
        //     steps{
        //         sh "env"
        //         sh "echo This step should run against non-main branches only"
        //         sh "echo PERFORMING LINT CHECKSS"
        //     }
        // }

        stage('Performing Ansible Dry Run'){
            when {
                 branch pattern: "PR-.*", comparator: "REGEXP"
            }
            steps{
            sh "env"
            sh "ansible-playbook -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW} -e COMPONENT=mongodb -e ENV=qa robo-dryrun.yaml"
        }
    }
        // stage('Promotion To Prod Branch'){
        //     when {
        //         branch pattern: "main"
        //     }
        // }
}
}