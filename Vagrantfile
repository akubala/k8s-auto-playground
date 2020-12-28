# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  config.vm.define "master" do |master|
    master.vm.box = "debian/buster64"
    master.vm.hostname = "master.local"

    master.vm.network "private_network",
      type: "dhcp"

    master.vm.network "public_network",
      bridge: "wlp2s0",
      ip: "192.168.1.200",
      netmask: 24

    master.vm.provision "ansible" do |ansible|
      ansible.playbook = "provision/playbook.yml"
      config_file = "ansible.cfg"
    end

    master.vm.post_up_message = "[OK] MASTER NODE"
  end

end
