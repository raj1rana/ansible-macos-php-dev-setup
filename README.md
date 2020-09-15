# Ansible mac setup

### requirements
1. python 3.X +
2. Ansible


### usges
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

# mysql variables
# always be root
mysql_user: root
# what you want to be the MYSQL password,
mysql_password:
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
          # hostname of the host mechine
          ansible_host:
          # ssh_password
          ansible_ssh_pass:
          # ssh username
          ansible_user:
          # sudo password
          ansible_sudo_pass:

    ungrouped: { }
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

