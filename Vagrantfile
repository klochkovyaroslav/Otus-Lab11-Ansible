# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure(2) do |config|
  # Centos7
    config.vm.define "server1-centos" do |cnt|
    # имя виртуальной машины в гепервизоре
    cnt.vm.box = 'centos/7' 
    cnt.vm.provider "virtualbox" do |vb|
      vb.name = "server1-centos"
    end
    # имя виртуальной машины в системе
    cntvm.hostname = "server1-centos"
    # настройки сети
    cnt.vm.network "private_network", ip: "192.168.56.150"
    cnt.vm.synced_folder ".", "/vagrant",  
          type: "rsync",
          rsync_auto: "true",
          rsync_exclude: [".git/",".vagrant/",".gitignore","Vagrantfile"]
          #cnt.vm.provision "shell", path: "provision/prepare-host.sh"
    end

  # Ubuntu
    config.vm.define "server2-ubuntu" do |ubnt|
    # имя виртуальной машины в гепервизоре
    ubnt.vm.box = 'ubuntu/trusty64' 
    ubnt.vm.provider "virtualbox" do |vbc|
      vbc.name = "server2-ubuntu"
    end
    # имя виртуальной машины в системе
    ubnt.vm.hostname = "server2-ubuntu"
    # настройки сети
    ubnt.vm.network "private_network", ip: "192.168.56.151"
    ubnt.vm.synced_folder ".", "/vagrant",  
          type: "rsync",
          rsync_auto: "true",
          rsync_exclude: [".git/",".vagrant/",".gitignore","Vagrantfile"]
          # Публичный ключ для ssh
  config.vm.provision "shell", inline: <<-SHELL
  cat /vagrant/provision/vagrant-key.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL

    end
end