# Ansible script for Odoo

Let's automate the installation of odoo with the help of very simple Ansible script. This playbook will help you to install Odoo (9.0).

## Getting Started

Following instructions will help you guide for the necessary steps for installation. Just clone the repo.

### Prerequisites

You will need to install Ansible in order to run the play. For ubuntu/iOS we will be using pip since it will go with both. You can still install Ansible using the system package.

### Installing

Using pip

```
sudo apt-get install python-pip #to install pip 
```
The standard that I follow is I create seprate folder for Codes and Installs. As it makes more sense to segregate Code and Installation files

So create Installs directory in your home directory. Then in Installs create envs, for pip virtual environments. Then create virtual env with in your env directory with,
You can read more about [pip](https://pip.pypa.io/en/stable/reference/pip_download/)
```
virtualenv ansible #to create env
pip install ansible #to install latest version of the ansible
```
Then just create two files
```
sudo mkdir /etc/ansible
sudo touch /etc/ansible/ansible.cfg
sudo touch /etc/ansible/hosts
```
######  Note: If you are a iOS user then pip is the preferred method.   
If you prefer not to use pip and want to you system packages then, you can install with, 
```
sudo apt-get install ansible 
```
###### Note: If you user apt-get to Install Ansible then you will by default have ansible.cfg and hosts file in /etc/ansible/ directory
Thats it. We are done with the installation part of the Ansible.

Edit ansible.cfg with the following paramaters
```
[defaults]

# some basic default values...

inventory      = /etc/ansible/hosts
remote_tmp     = $HOME/.ansible/tmp
pattern        = *
forks          = 5
poll_interval  = 15
sudo_user      = root
ask_sudo_pass = True
#ask_pass      = True
transport      = ssh
remote_port    = 22

[ssh_connection]
ssh_args = -o ForwardAgent=yes -o ControlMaster=auto -o ControlPersist=60s
```

Create your own host in hosts file.
```
[server_name]
server_ip or ips
```

## Creating your own SSH keys
If you havent created your own private keys create using the following command and select the directories to save it in or skip to stick with deafault. Similarly you need to do on the server if not created.
```
ssh-keygen -t rsa
```

Copy your private key in the .ssh directory ie id_rsa.pub file, if default path is selected then it will be in 
```
cat ~/.ssh/id_rsa.pub 
```
Paste the same in the your ansible Hosts in authorized_keys, it wont be created by default
On every host,
```
nano ~/.ssh/authorized_keys
#paste the copied private key in this file.
```
## Running the Play

After all this hustle, we are finally ready to run the play, go to taks directory in the playbook 
```
ansible-playbook -v main.yml --extra-vars "odoo_version=9.0 host_name=your_server_name user_name=your_user_name"
```
The good reason to put extra vars it that we can change the version for Odoo(below 10) and host on the go whenever we want.

Thats it. Tried and tested on version 9 and 8. For now it wont suppoert 10 as the installation steps are quite different.


## Built With

* [Ansible](https://ansible.com/) - Simple IT automation tool


## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.


## Authors

* **Jitendra Varma** - DevOps at  - [Fafadiatech](https://fafadiatech.com/)


## License

This project is licensed under the standard MIT License

## Acknowledgments

* Thanks to [Yogesh Panchal](https://github.com/yspanchal) and [Sidharth Shah](https://github.com/sidharthshah) for their support
