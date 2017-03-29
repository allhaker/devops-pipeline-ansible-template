# Management Node with Rancher Provisioner
Minimal Rancher installation for Debian Jessie with Docker.

## Prerequisites

*    [Ansible](http://docs.ansible.com/ansible/intro_installation.html)
*    [Vagrant](https://www.vagrantup.com/downloads.html)
*    Docker Images must be updloaded to [Eficode Artifactory](https://efifactory.eficode.fi) or another Docker repository

## What is installed (configured)

*   Docker
*   Rancher as Docker container
*   Added a 2G swap file
        
## Run With Vagrant
The command below would start up a vagrant machine and Vagrant will try to install Ansible automatically on your system. When completed, Rancher will be available at [192.168.50.5:8888](http://192.168.50.5:8888)

    `sudo vagrant up`

## Run With Ansible Only
If you would like to provision a real server with Ansible, enter the commands below:

    `cd ansible/`
    `sudo ansible-playbook --ask-pass -u root provision.yml`

Ansible would prompt ssh password - remove `--ask-pass` if you are not using it.
    
## Set up Rancher
1. Access Rancher at [192.168.50.5:8080](http://192.168.50.5:8080)
2. On the first screen click `Add Host`
3. This step is very important. Rancher will ask you to set a Rancher URL or IP. We *strongly suggest*  to use your server IP rather than URL. Setting URL as Rancher path may cause Rancher to not function. 
`DO NOT try to set Rancher path to  localhost - Rancher WILL NOT WORK!`  Anyway, set Rancher path to an IP and press `Save`
4. On the next page enter your host address (192.168.50.5 in Vagrant case) into `textfield 4`
5. Copy Docker command available just below and insert it into Terminal of the host where Rancher is running. Then click `close`.
6. You should see your Host on Hosts page shortly.
2. Go to `Infrastucture` tab and click `Add Registry` there

4. Select `Docker Hub` in case you are using it.
5. Then go to `Stacks` - `All` and click `Add Stack`
6. Name your new Stack and updload `docker-compose-swarm.yml` file, then click `Create`.
7. That is it! Rancher will now set up your new Service.
