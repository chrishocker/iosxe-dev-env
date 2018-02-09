# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "iosxe/16.06.02"

  config.vm.network "forwarded_port", guest: 5000, host: 5000

  # nic_type: "virtio" needed for IOS XE 16.7+
  config.vm.network :private_network, virtualbox__intnet: "link1", auto_config: false
  config.vm.network :private_network, virtualbox__intnet: "link2", auto_config: false

#  config.vm.provision "ansible" do |ansible|
#    ansible.playbook = "ansible/playbooks/ansible_provision.yaml"
#    ansible.inventory_path = "./ansible/hosts"
#  end

end
