# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure(2) do |config|
  # Centos7
    config.vm.define "server1-centos" do |cnt|
    # имя виртуальной машины
    cnt.vm.box = 'centos/7' 
    cnt.vm.provider "virtualbox" do |vb|
      vb.name = "server1-centos"
    end
    # hostname виртуальной машины
    server.vm.hostname = "server1-centos"
    # настройки сети
    server.vm.network "private_network", ip: "192.168.56.150"
    server.vm.synced_folder ".", "/vagrant",  
          type: "rsync",
          rsync_auto: "true",
          rsync_exclude: [".git/",".vagrant/",".gitignore","Vagrantfile"]
          #server.vm.provision "shell", path: "provision/prepare-host.sh"
    end

  # Ubuntu
    config.vm.define "server2-ubuntu" do |ubnt|
    # имя виртуальной машины
    ubnt.vm.box = 'ubuntu/trusty64' 
    ubnt.vm.provider "virtualbox" do |vbc|
      vbc.name = "server2-ubuntu"
    end
    # hostname виртуальной машины
    client.vm.hostname = "server2-ubuntu"
    # настройки сети
    client.vm.network "private_network", ip: "192.168.56.151"
    client.vm.synced_folder ".", "/vagrant",  
          type: "rsync",
          rsync_auto: "true",
          rsync_exclude: [".git/",".vagrant/",".gitignore","Vagrantfile"]
          #client.vm.provision "shell", path: "provision/prepare-host.sh"
# ssh-pub add in server
  config.vm.provision "shell", inline: <<-SHELL
  cat /vagrant/provision/vagrant-key.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL

    end
end