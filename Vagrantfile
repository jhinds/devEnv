# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  for i in 48000..48900
    config.vm.network "forwarded_port", guest: i, host: i
  end  

  config.vm.post_up_message = "To finish installing the ansible play run \"source ./hacking/env-setup\" "
  # config.vm.provider = "virtualbox"

  config.vm.provision "docker"
  config.vm.provision "ansible" do |ansible|
    # ansible.playbook = "plays/nodejs.yml"
    # ansible.playbook = "plays/git.yml"
    ansible.playbook = "plays/ansiblesource.yml"
    # ansible.playbook = "plays/ruby.yml"
  end

  config.vm.network :private_network, ip: "192.168.0.234"

end

