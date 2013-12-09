# -*- mode: ruby -*-
# vi: set ft=ruby :

#vagrant
Vagrant.configure("2") do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://vagrant.corp.anjuke.com/boxes/precise32.box"
  config.vm.network :private_network, ip: "192.168.127.2"

  config.vm.provision :shell,
    inline: "mkdir -p /root/.ssh && cp /home/vagrant/.ssh/authorized_keys /root/.ssh/"

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "provisioning/hosts.vagrant"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.verbose = 'vvvv'
  end

end

