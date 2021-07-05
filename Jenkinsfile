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
                        whoami
                        cd ansible && ansible-playbook -u root ./playbooks/ping.yml -i inventory.txt
                    '''
                }
            }
        }
        stage ('Test') {
            steps {
                echo 'Running Test phase. '
            }
        }
        stage ('QA') {
            steps {
                echo 'Running QA phase. '
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Running Deploy phase. '
            }
        }

    }
 }
