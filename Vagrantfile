# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # ubuntu image that I use. Can be found at https://atlas.hashicorp.com/ubuntu/boxes/trusty64
  config.vm.box = "ubuntu/trusty64"

  # this should be used to make virtual box your provider.  vagrant yells at me when I include this though.
  # config.vm.provider = "virtualbox"

  # the network ip address for the virtual machine
  config.vm.network :private_network, ip: "192.168.0.234"

  # range of ports that are fowarded between the guets and host
  for i in 48000..48900
    config.vm.network "forwarded_port", guest: i, host: i
  end  

  #This is the default port mongodb connects to
  config.vm.network "forwarded_port", guest: 27017, host: 27017

  # this install docker on the VM
  config.vm.provision "docker"

  # this are where the ansible plays live (or should) that installs everything on the VM 
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vagrant-env-playbook/main.yml"
  end

  # this message pops up after you run a vagrant up.  I added it here for a reminder to myself since I still haven't found a way to automate this.  
  config.vm.post_up_message = "To finish installing ansible run \"source ./hacking/env-setup\" after you ssh into the machine"

end
