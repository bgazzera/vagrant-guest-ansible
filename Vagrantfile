# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.network "private_network", ip: "192.168.50.4",
    virtualbox__intnet: true

  config.vm.network "private_network", ip: "192.168.56.4"

 
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "512"
  end
 

  if Vagrant::Util::Platform.windows?
    config.vm.provision :guest_ansible do |ansible|
      ansible.playbook = "provision/setup.yml"
      ansible.sudo = true
    end
  else
    config.vm.provision :ansible do |ansible|
      ansible.playbook = "provision/setup.yml"
      ansible.sudo = true
    end
  end

  config.putty.session = "vagrant"
end
