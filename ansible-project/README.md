## Establishing a passwordless SSH connection between AWS EC2 instances using Ansible
#### I have created 3 Ec2 instances with the same key pair.
![Screenshot-2024-01-16-222734.png](https://i.postimg.cc/HnyXg698/Screenshot-2024-01-16-222734.png)
#### Now login to the ansible master by mobaxterm using ssh
* `ssh -i "ansiblepem.pem" Public IPv4 DNS`
#### Update the system
* `sudo apt update`

![Screenshot-2024-01-16-005244.png](https://i.postimg.cc/kXJ5QjkJ/Screenshot-2024-01-16-005244.png)
#### Install ansible
* `sudo apt install ansible -y`

![Screenshot-2024-01-16-005334.png](https://i.postimg.cc/MTXLJf3f/Screenshot-2024-01-16-005334.png)
#### Create a New User on Ansible Master and set a password
* `sudo -i`
* `useradd -m -s /bin/bash testuser`
* `passwd testuser`

![Screenshot-2024-01-16-005917.png](https://i.postimg.cc/nVvpr6cR/Screenshot-2024-01-16-005917.png)
####  Add the user to sudoers and grants passwordless sudo privileges to the user
* `echo -e 'testuser\tALL=(ALL)\tNOPASSWD:\tALL' > /etc/sudoers.d/testuser`

![Screenshot-2024-01-16-010108.png](https://i.postimg.cc/508BZxqW/Screenshot-2024-01-16-010108.png)
#### Log in as the testuser user
* `sudo -su testuser`
#### Generate SSH Keys for the testuser
* `ssh-keygen`

![Screenshot-2024-01-16-010709.png](https://i.postimg.cc/RF9hZfnh/Screenshot-2024-01-16-010709.png)
#### Copy the id_rsa.pub file to a location accessible by the Ansible playbook
* `cd ~/.ssh`

![Screenshot-2024-01-16-010801.png](https://i.postimg.cc/KYJ0v71v/Screenshot-2024-01-16-010801.png)
#### Add pem file and change the permission of the pem file
* `sudo chmod 600 test.pem`

![Screenshot-2024-01-16-020554.png](https://i.postimg.cc/cJD5cvpH/Screenshot-2024-01-16-020554.png)
#### Clone Repository
* `git clone https://github.com/iamarbabkhan/ansible.git`

![Screenshot-2024-01-16-012219.png](https://i.postimg.cc/JnL0zF2j/Screenshot-2024-01-16-012219.png)
#### Now run the playbook
* `ansible-playbook main.yml -i inventory/hosts --user ubuntu --key-file test.pem -e '@configs/user.yml`

![Screenshot-2024-01-16-040255.png](https://i.postimg.cc/FFpSTwGY/Screenshot-2024-01-16-040255.png)
![Screenshot-2024-01-16-040336.png](https://i.postimg.cc/fWGV2BZ4/Screenshot-2024-01-16-040336.png)
