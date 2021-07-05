pipeline {
agent any
    stages {
        stage ('Ping') {
            steps {
                echo 'Running ping phase. '
                withCredentials([usernamePassword(credentialsId: 'aws_win_1_creds',
                     passwordVariable: 'winPass', usernameVariable: 'winUser')]) {

                    // the code here can access $winPass and $WinUser
                    sh '''#!/bin/bash
                        echo "hello world from bash"
                        export WIN_USR=$winUser
                        export WIN_PWD=$winPass
                        printenv
                        cd ansible && ansible-playbook ./playbooks/ping.yml -i inventory.txt
                    '''
                }
            }
        }
        stage ('Update') {
            steps {
                echo 'Running Update phase. '
                sh '''#!/bin/bash
                        echo "hello world from bash"
                        printenv
                        cd ansible && ansible-playbook ./playbooks/winupdt.yml -i inventory.txt
                    '''
            }
        }

    }
 }
