# -*- mode: ruby -*-

# vi: set ft=ruby :

Vagrant.require_version ">= 1.7"

Vagrant.configure(2) do |config|

  config.ssh.insert_key = false
  config.vm.box = "centos/7"

  config.vm.hostname = "BF1"
  config.vm.define :BF1 do |t| 
  end 

  config.vm.network :private_network, type: "dhcp"
  config.vm.network :forwarded_port, guest: 80, host: 8080, auto_correct: true

# for reference | https://www.virtualbox.org/manual/ch08.html#idm3626
  config.vm.provider "libvirt" do |v| 
    v.memory = 5192
    v.cpus = 2 
    v.nested = true
    v.volume_cache = 'none'
  end 
  config.vm.provider "virtualbox" do |v| 
    v.customize ["modifyvm", :id, "--name", "BF1"]
    v.customize ["modifyvm", :id, "--cpus", "2"]
    v.customize ["modifyvm", :id, "--memory", "5192"]
  end 
  config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "vvv"
    ansible.playbook = "playbook.yml"
  end 

  config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "vvv"
    ansible.playbook = ENV['BREAKTASKFILE']
  end 

end
