pipeline {
agent any
    stages {
        stage ('Build') {
            steps {
                echo 'Running build phase. '
                sh '''#!/bin/bash
                    echo "hello world"
                    ls
                    whoami
                '''
                ansible-playbook ./ping.yml -i hosts
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
