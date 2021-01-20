# Ansible playbook for MediaWiki

## General

Only tested using Ubuntu 18.04 for host and remote host.

## Notes

For authentication, we use an ssh key located at ```~/terraform_key```.

Default credentials for the MediaWiki can be found and changed [here](./roles/mediawiki/defaults/main.yml)

## Pre-Installation

### Install Ansible

Install ansible on **both** the main server and the remote server:

```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

### Add Remote Server's IP to Main Server's host list

Now add the IP of the remote host on your main host ansible hosts list:

```
$ sudo nano /etc/ansible/hosts
+ 192.168.151.2
```

As an example, we will use ```192.168.151.2``` as the IP of the remote host.

### Install Ansible's MySQL plugin

On the Main Server:

```
$ ansible-galaxy collection install community.mysql
```

## Run the Playbook

```
$ ansible-playbook playbook.yml --private-key ~/terraform_key
```





