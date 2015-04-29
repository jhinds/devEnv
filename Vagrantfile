# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  # for i in 48000..48900
  #   config.vm.network "forwarded_port", guest: i, host: i
  # end  

  # config.vm.network "forwarded_port", guest: 27017, host: 27017



  config.vm.post_up_message = "To finish installing the ansible play run \"source ./hacking/env-setup\" "
  # config.vm.provider = "virtualbox"

  # config.vm.provision "docker"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vagrant-env-playbook/main.yml"
  end

  config.vm.network :private_network, ip: "192.168.0.234"

end
