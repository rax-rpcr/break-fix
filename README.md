# break-fix

These scripts will build a basic all in one VM running RDO Packstack. Purpose of these scripts to to give you a starting point to start creating "break/fix" scenerios for the team competition.

The individual breakfix playbooks are in the `breaks` sub-directory.  The top few lines of each playbook contain a hint, if needed.  Looking past the first few lines before solving the problem will spoil the exercise and bring you bad openstack karma.

### Requirements for your machine:

### If you prefer to use VirtualBox for your virtual machine:

 1. **Virtualbox** ([https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads))

### If you prefer to use libvirt for your virtual machine:

 1. **Libvirt** ([https://libvirt.org/])
 2. **Libvirt Vagrant Plugin** ([https://github.com/vagrant-libvirt/vagrant-libvirt])
 3. **Vagrant Mutate Plugin** ([https://github.com/sciurus/vagrant-mutate])

### If you prefer to use a Rackspace cloud server for your virtual machine:

 1. $ vagrant plugin install vagrant-rackspace
 2. **Rackspace Vagrant Plugin** ([https://github.com/mitchellh/vagrant-rackspace])

### Mandatory Software for your physical system (whichever virtualization engine you choose to use for your virtual machine):
 1. **Git** ([https://git-scm.com/downloads](https://git-scm.com/downloads))
 2. **Vagrant** ([https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html))
 3. **Vagrant Sahara Plugin** ([https://github.com/jedi4ever/sahara])
 3. **Ansible** ([http://docs.ansible.com/ansible/intro\_installation.html](http://docs.ansible.com/ansible/intro_installation.html))

### Resources required on your physical system:
 1. 6GB RAM
 2. 2vcpu
 3. 10GB disk

### Deploying a Lab:
 1. Make sure all requirements are met above. Regarding the virtualization engine, both VirtualBox and libvirt are supported so you could choose whichever works best for you.
 2. git clone http://github.com/rax-rpcr/break-fix
 3. cd break-fix
 4. Create a randomly selected breakfix by running:

    \# ./breakfix

    OR select a specific breakfix excercise:

    \# ./breakfix breaks/breakXXX.yml (for example: ./breakfix breaks/break000.yml)
 5. Building the breakfix environment takes 20-30 minutes.  The final output will inform you about what is broken.
 6. Log in via ssh "`ssh root@127.0.0.1 -p 2222`" with password "rpcr". Access Horizon via [http://127.0.0.1:8080/dashboard](http://127.0.0.1:8080/dashboard)  (user credentials may be found in the /root/keystonerc\* files in the VM)
 7. Away you go!

### Cleaning up a lab when you are done:
 1. Capture/Document any needed information from the breakfix environment.
 2. Run "`./breakfix-cleanup`" to delete the VM.

### Adding a new breakfix exercise:
 1. Create a new /breaks/breakXXX.yml playbook file using the next available sequence number.  It is suggested that you copy an existing breakXXX.yml file and modify it to implement your exercise.
