# break-fix

These scripts will build a basic all in one VM running RDO Packstack. Purpose of these scripts to to give you a starting point to start creating "break/fix" scenerios for the team compitition.

Requirements for your machine:
1. Virtualbox
2. Vagrant
3. Ansible
 
Virtualbox Install:
https://www.virtualbox.org/wiki/Downloads

Vagrant Install:
https://www.vagrantup.com/downloads.html

Ansible Install:
http://docs.ansible.com/ansible/intro_installation.html
or
Install EPEL: http://fedoraproject.org/wiki/EPEL
sudo yum install ansible

Deploying a Lab:
1. Make sure all requirements are met above
2. git clone http://github.com/rax-rpcr/break-fix
3. cd break-fix
4. run "vagrant up"
5. Log in via ssh "ssh root|stack@127.0.0.1 -p 2222"
6. Away you go!
