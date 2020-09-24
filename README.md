# Ansible mac setup

### Install brew on target system 
```sh 
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```



### requirements
1. python 3.X +
2. Ansible
3. sshpass

### usages
```sh
$ git clone https://git.ithands.com/robert.rajendra/ansible-mac-os-setup.git
$ cd ansible-mac-os-setup
$ cp hosts.example.yml hosts.yml
$ cp vars/env.example.yml vars/env.yml
```

### env.yml
```sh
# env located in var/env.yml
# versions
# eg:- 5.7, 5.8
mysql_version:
# eg:- 7.1, 7.2, 7.3, 7.4
php_version:

# http variables
# document root for the app (must be your project folder)
document_root:
# username of the user
username:
# group of the user, Please check which group in older MAC os it is "admin"
group:


```
### hosts.yml
```sh
# This file is the inventory file this file contains the the information about hosts
all:
  children:
    setup_macos:
      hosts:
        # this is an ansible host you can create more hosts
        mac:
          ansible_connection: ssh
          # IP of the host machine
          ansible_host:
          # ssh_password
          ansible_ssh_pass:
          # ssh username
          ansible_user:
          # sudo password
          ansible_sudo_pass:

    ungrouped: { }
```

### Run ansible
```sh 
ansible-playbook -v playbook.yml
```


### Go to target system 
run these commands 
```sh
brew services start --all
apachectl -k start
```
### Initial mysql password is none please set it by 
```sh 
mysql -u root -p
alter user 'root'@'localhost identified by '<your password';
flush privileges;
```

### NOTE 

for coloured comments install better comnents for vscode from https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments