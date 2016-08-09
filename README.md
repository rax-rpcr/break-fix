# break-fix

These scripts will build a basic all in one VM running RDO Packstack. Purpose of these scripts to to give you a starting point to start creating "break/fix" scenerios for the team competition.

The individual breakfix playbooks are in the `breaks` sub-directory. Looking past the first few lines before solving the problem will spoil the exercise and bring you bad openstack karma.

### Requirements for your machine:

### If you prefer to use VirtualBox for your virtual machine:

 - **Virtualbox** ([https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads))

### If you prefer to use libvirt for your virtual machine:

 - **Libvirt** (https://libvirt.org/)
 - **Libvirt Vagrant Plugin** (https://github.com/vagrant-libvirt/vagrant-libvirt)

### If you prefer to use a Rackspace cloud server for your virtual machine:

 - **Rackspace Vagrant Plugin** (https://github.com/mitchellh/vagrant-rackspace)

### Mandatory Software for your physical system (whichever virtualization engine you choose to use for your virtual machine):
 - **Git** ([https://git-scm.com/downloads](https://git-scm.com/downloads))
 - **Vagrant** ([https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html))
 - **Vagrant Sahara Plugin** (https://github.com/jedi4ever/sahara)
 - **Vagrant fog Plugin** (https://github.com/fog/fog-libvirt)
 - **Ansible** version 2 or newer ([http://docs.ansible.com/ansible/intro\_installation.html](http://docs.ansible.com/ansible/intro_installation.html))

### Resources required on your physical system if you use libvirt or VirtualBox:
 - 6GB RAM
 - 2vcpu
 - 10GB disk

### Setup prior to deploy your first lab

###### Run the following commands with the user you are going to run your environment:
```
$ vagrant plugin install fog
$ vagrant plugin install sahara
```
###### If you decide to use libvirt:
```
$ vagrant plugin install vagrant-libvirt
```
###### If you decide to use rackspace cloud:
```
$ vagrant plugin install vagrant-rackspace
$ export RAX_USERNAME=<your cloud username>
$ export RAX_API_KEY=<your api key>
$ export RAX_REG=<your rackspace cloudregion>
``` 
###### If you decide to use VirtualBox:
Vagrant VirtualBox is out of the box, so #youshouldnotworry

### Deploying a Lab:

 1. Make sure all requirements are met above.
 2. `git clone http://github.com/rax-rpcr/break-fix`
 3. `cd break-fix`
 4. Create a randomly selected breakfix by running:

    $ `./breakfix`

    OR select a specific breakfix exercise:

    $ `./breakfix breaks/break*XXX*.yml` (for example: `./breakfix breaks/break000.yml`)

 5. The first time you deploy your lab, the scripts are going to build the breakfix environment. Building the breakfix environment takes 20-30 minutes. Then, the scripts will take a snapshot and will rollback to it for the following exercises.
 6. The final output will inform you about where you can find info about the exercise.
 7. Capture/Document any needed information from the breakfix environment.

### Notes:

During the build it could happen that the CentOS repositories become unavailable or fails the OpenStack all-in-one installation. If that's the case, the script will retry to redeploy the ansible playbook until it's succesful. If something else besides that is broken, the script will exit. In such scenario, just rerun the script until the exit is succesfull and/or run `./breakfix-cleanup` if required.

### Cleaning up after you are done with all your labs:

Run "`./breakfix-cleanup`" to delete the VM.

### Want to participate? Adding a new breakfix exercise:

Create a new `breaks/breakXXX.yml` playbook file using the next available sequence number.  It is suggested that you copy an existing `break000.yml` (which is the current standard and contains the instructions how to build your own breaks) and modify it to implement your exercise.
