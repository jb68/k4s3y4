# Jenkins + Ansible + Windows

### Infrastructure:
This require a Github repository, a jenkins server and a windows server
- **Github**
  - [x] Create new repository
- **Jenkins**
  - [x] Build Jenkins Server at http://f1.jb68.com:8080
    ```
    docker run -d --name jbjenkins -p 8080:8080 -p 50000:50000 -v /data/jenkins:/var/jenkins_home jenkins/jenkins:lts
    ```
  - [x] Configure users
- **Windows AWS**
  - [x] install an windoze server 4 free on AWS
      https://aws.amazon.com/premiumsupport/knowledge-center/free-tier-windows-instance/
  - [x] test connection rdp from @home
  - [x] restart windows and recheck

### Automation
- **Github**
  - [x] Add Webhook to point to jenkins instance
- **Jenkins**
  - [x] Configure 1 normal job and 1 pipline job
  - [x] Configure jenkins to work with GH for normal job
  - [x] Configure Jenkins to listen to GH to trigger normal job
  - [x] Configure Jenkins to pull jenkinsfile from GH for pipline
  - [x] Configure Jenkins to listen to GH to trigger PL
- **Ansible**
  - [x] Install ansible on jenkins slave docker ( same as jenkins server )
    ```bash
    docker run -it -u 0 jbjenkins bash
    apt update; apt install python ansible openssh-client vim iputils-ping -y
    ```
  - [x] test Ansible manually from docker container
    ```
    docker exec -it -u 0 jbjenkins bash
    su jenkins
    ansible-playbook -u root ./playbooks/ping.yml -i inventory.txt
    ```
  - [x] test automation, push to GH will run Ansible on Jenkins
- **Windows AWS**
  - [x] add Ansible client
  - [x] check listener ps command: winrm enumerate winrm/config/Listener  
  Note: on AWS public IP is not on device, it is on firewall. PublicIP -> Firewall -> PrivateIP(device)
  - [x] Set firewall add port 5985, 5986
- **Ansible**
  - [x] create windows inventory and playbook file for ping, update, reboot
  - [x] check connection to windoze `ansible windows2019 -i inventory.txt -m win_ping`
  - [x] swich to use env variables for WIN_IP, WIN_PWD, WIN_USR
  - [x] fix ping playbooks
  - [x] test update plybooks
- **Jenkins**
  - [x] update and clean jenkinsfile
  - [x] create kaseya user in Jenkins


## TODO
- [x] improve doc
- [ ] docker-compose for jenkins server & slaves
- [ ] docker files for jenkins slaves
- [ ] test jenkins setup
- [ ] multiple servers on ansible
