# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.provider :virtualbox do |vb|
    vb.gui = true
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box     = "ubuntu1404"
    ubuntu.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box"

    ubuntu.ssh.forward_agent = true
    ubuntu.vm.network "private_network", ip: "192.168.33.10"

    ubuntu.vm.provision 'ansible' do |ansible|
      ansible.inventory_path = 'inventories/hosts'
      ansible.playbook = 'site.yml'
      ansible.limit = 'all'
      # ansible.verbose = 'vvvv'
    end
  end
end
