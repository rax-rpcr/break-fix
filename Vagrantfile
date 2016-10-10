# -*- mode: ruby -*-

# vi: set ft=ruby :

Vagrant.require_version ">= 1.7"

Vagrant.configure(2) do |config|

  config.ssh.insert_key = false
  config.ssh.pty = true
  # If needed, uncomment the line below and replace $BASTION with your bastion server.
  # config.ssh.proxy_command = "ssh -A $BASTION nc %h %p"

  config.vm.box = "centos/7"

  #config.vm.hostname = "BF1"
  #config.vm.define :BF1 do |t|
  #end

  config.vm.network :private_network, type: "dhcp"
  config.vm.network :forwarded_port, guest: 80, host: 8080, auto_correct: true

  config.vm.provider :rackspace do |rs|
    rs.username         = ENV['RAX_USERNAME']
    rs.api_key          = ENV['RAX_API_KEY']
    rs.rackspace_region = ENV['RAX_REG']
    rs.flavor           = /8 GB General Purpose v1/
    rs.image            = "76718f32-54af-43a7-bfa2-bf314d4765e3"
    rs.init_script = 'sed -i\'.bk\' -e \'s/^\(Defaults\s\+requiretty\)/# \1/\' /etc/sudoers'
  end

  config.vm.provider :libvirt do |v|
    v.memory = 6144
    v.cpus = 2
    v.nested = true
    v.volume_cache = 'none'
    v.storage_pool_name = 'default'
  end

  # for reference | https://www.virtualbox.org/manual/ch08.html#idm3626
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--name", "BF1"]
    v.customize ["modifyvm", :id, "--cpus", "2"]
    v.customize ["modifyvm", :id, "--memory", "8192"]

  end
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vvv"
#    ansible.playbook = "playbook.yml"
#    ansible.playbook = "newton.yml"
    ansible.playbook = "mitaka.yml"
#    ansible.playbook = "liberty.yml"
#    ansible.playbook = "kilo.yml"

  end

end
