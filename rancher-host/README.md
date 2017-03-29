# Management Node with Rancher Provisioner
Minimal Rancher worker installation for Debian Jessie with Docker.

## Prerequisites

*    [Ansible](http://docs.ansible.com/ansible/intro_installation.html)
*    [Vagrant](https://www.vagrantup.com/downloads.html)

## What is installed

*   Docker
*   Added a 2G swap file
        
## Run With Vagrant
The command below would start up a vagrant machine and Vagrant will try to install Ansible automatically on your system. When complete Rancher will be available at [192.168.50.5:8888](http://192.168.50.5:8888)

    `sudo vagrant up`

## Run With Ansible Only
If you would like to provision a real server with Ansible, enter the commands below:

    `cd ansible/`
    `sudo ansible-playbook --ask-pass -u root provision.yml`

Ansible would prompt ssh password - remove `--ask-pass` if you are not using it.
