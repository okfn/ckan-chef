# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.berkshelf.enabled = true
  config.berkshelf.berksfile_path = 'cookbooks/ckan/Berksfile'

  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  config.vm.hostname = 'default.ckanhosted.dev'
  config.vm.network :private_network, ip: '192.168.42.42'

  config.vm.network "forwarded_port", guest: 8983, host: 8983
  config.vm.network "forwarded_port", guest: 5000, host: 5000  # paster server (development)

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ['cookbooks']
    chef.run_list = [
      "recipe[ckan::2.3_install]",
    ]
  end
end
