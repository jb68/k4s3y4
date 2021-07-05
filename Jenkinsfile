pipeline {
agent any
    stages {
        stage ('Windows Update') {
            steps {
                echo 'Starting Update phase.'
                withCredentials([usernamePassword(credentialsId: 'aws_win_1_creds',
                     passwordVariable: 'WIN_PWD', usernameVariable: 'WIN_USR')]) {
                    sh '''#!/bin/bash
                            echo "Running Ansible Update"
                            cd ansible && ansible-playbook ./playbooks/winupdt.yml -i inventory.txt
                        '''
                    }
            }
        }
        stage ('Ping Check') {
            steps {
                echo 'Starting ping phase.'
                withCredentials([usernamePassword(credentialsId: 'aws_win_1_creds',
                     passwordVariable: 'WIN_PWD', usernameVariable: 'WIN_USR')]) {

                    // the code here can access $winPass and $WinUser
                    sh '''#!/bin/bash
                        echo "Running Ansible ping"
                        cd ansible && ansible-playbook ./playbooks/ping.yml -i inventory.txt
                    '''
                }
            }
        }

    }
 }
