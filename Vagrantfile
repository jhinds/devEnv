# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # ubuntu image that I use. Can be found at https://atlas.hashicorp.com/ubuntu/boxes/trusty64
  config.vm.box = "ubuntu/trusty64"

  # could be used to stop the /etc/resolv.conf from being overridden on restart
  # config.vm.provider :virtualbox do |vb|
  #   vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  # end

  # the network ip address for the virtual machine
  config.vm.network :private_network, ip: "192.168.0.234"

  # range of ports that are fowarded between the guets and host
  for i in 48000..48900
    config.vm.network "forwarded_port", guest: i, host: i
  end  

  # this is the default port mongodb connects to
  config.vm.network "forwarded_port", guest: 27017, host: 27017

  config.vm.network "forwarded_port", guest: 8080, host:8080 
  config.vm.network "forwarded_port", guest: 3000,  host: 3000, auto_correct: true  # rails application
  config.vm.network "forwarded_port", guest: 3306,  host: 3307, auto_correct: true  # mysql
  config.vm.network "forwarded_port", guest: 5432,  host: 5532, auto_correct: true  # postgresql

  # this install docker on the VM
  config.vm.provision "docker"

  # this are where the ansible plays live (or should) that installs everything on the VM 
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vagrant-env-playbook/site.yml"
  end

  # this message pops up after you run a vagrant up.  I added it here for a reminder to myself since I still haven't found a way to automate this.  
  config.vm.post_up_message = "To finish installing ansible run \"source ./hacking/env-setup\" after you ssh into the machine"

end
