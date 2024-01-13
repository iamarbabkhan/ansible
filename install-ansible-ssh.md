## install ansible and ssh on linux

#### Step1
From master node
* `sudo apt update`
* `sudo apt install software-properties-common`
* `sudo apt-add-repository --yes --update ppa:ansible/ansible`
* `sudo apt install ansible`

#### Step2
From worker node
* `sudo apt update`
* `sudo apt install python3`

#### Step3
From master node
* `cat ~/.ssh/id_rsa.pub`

#### Step4
From worker node
* paste the key to `~/.ssh/authorized_keys`

#### Step5
From master node
* `ssh ipofnode`
* `exit`
* `sudo vi /etc/ansible/hosts`
1. [groupname]
2. nodename ansible_ssh_host=ipofnode
3. nodename ansible_ssh_host=ipofnode

#### Step6
* `ansible -m ping all`
or
* `ansible -m ping groupname`
or
* `ansible -m ping all nodename`
