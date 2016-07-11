# break-fix

These scripts will build a basic all in one VM running RDO Packstack. Purpose of these scripts to to give you a starting point to start creating "break/fix" scenerios for the team competition.

### Requirements for your machine:
 1. **Virtualbox** (`https://www.virtualbox.org/wiki/Downloads`)
 1. **Vagrant** (`https://www.vagrantup.com/downloads.html`)
 1. **Ansible** (`http://docs.ansible.com/ansible/intro_installation.html`)
 1. Resources to create the VM (6GB RAM, 2vcpu, 10GB disk)
 
### Deploying a Lab:
 1. Make sure all requirements are met above
 1. git clone http://github.com/rax-rpcr/break-fix
 1. cd break-fix
 1. run "vagrant up" (this may take 20+ minutes to complete)
 1. Log in via ssh "ssh root@127.0.0.1 -p 2222" with password "rpcr"
 1. Away you go!

### Cleaning up a lab when you are done:
 1. run "vagrant destroy" will delete the VM

### Adding a new breakfix exercise:
 1.
