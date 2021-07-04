# k4s3y4
test 4 k4s3y4

## Infrastructure
### Github
    - Create new repository
### Jenkins
    - Build Jenkins Server: Done at http://f1.jb68.com:8080
### Github
    - Add Webhook to point to jenkins instance
### Jenkins
    - Configure jenkins to work with GH for normal job: Done
    - Configure Jenkins to listen to GH to trigger normal job: Done
    - Configure Jenkins to pull jenkinsfile from GH: Done
    - Configure Jenkins to listen to GH to trigger PL : Testing
### Ansible
    - Install ansible on jenkins slave docker ( same as jenkins server )
    docker run -it -u 0 jbjenkins bash
    apt update; apt install python ansible openssh-client vim iputils-ping -y
    - test Ansible manually Done
    ansible-playbook -u root ./playbooks/ping.yml -i inventory.txt
    - test automation, push to GH will run Ansible on Jenkins - Done
### Windows
    - install a windoze server 4 free on AWS ?
