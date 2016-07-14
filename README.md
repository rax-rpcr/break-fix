# break-fix

These scripts will build a basic all in one VM running RDO Packstack. Purpose of these scripts to to give you a starting point to start creating "break/fix" scenerios for the team competition.

The individual breakfix playbooks are in the `breaks` sub-directory.  The top few lines of each playbook contain a hint, if needed.  Looking past the first few lines before solving the problem will spoil the exercise and bring you bad openstack karma.

### Requirements for your machine:
 1. **Git** ([https://git-scm.com/downloads](https://git-scm.com/downloads))
 1. **Virtualbox** ([https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads))
 1. **Vagrant** ([https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html))
 1. **Ansible** ([http://docs.ansible.com/ansible/intro\_installation.html](http://docs.ansible.com/ansible/intro_installation.html))
 1. Resources to create the VM (6GB RAM, 2vcpu, 10GB disk)
 
### Deploying a Lab:
 1. Make sure all requirements are met above
 1. git clone http://github.com/rax-rpcr/break-fix
 1. cd break-fix
 1. Create a randomly selected breakfix by running:

    \# ./breakfix
    
    OR select a specific breakfix excercise:
    
    \# ./breakfix breaks/breakXXX.yml (for example: ./breakfix breaks/break000.yml)
 1. Building the breakfix environment takes 20-30 minutes.  The final output will inform you about what is broken.
 1. Log in via ssh "`ssh root@127.0.0.1 -p 2222`" with password "rpcr". Access Horizon via [http://127.0.0.1:8080/dashboard](http://127.0.0.1:8080/dashboard)  (user credentials may be found in the /root/keystonerc\* files in the VM)
 1. Away you go!

### Cleaning up a lab when you are done:
 1. Capture/Document any needed information from the breakfix environment.
 1. Run "`./breakfix-cleanup`" to delete the VM.

### Adding a new breakfix exercise:
 1. Create a new /breaks/breakXXX.yml playbook file using the next available sequence number.  It is suggested that you copy an existing breakXXX.yml file and modify it to implement your exercise.
