# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure(2) do |config|
  # Centos7
    config.vm.define "server1-centos" do |cnt|
        cnt.vm.box = 'centos/7' 
    cnt.vm.provider "virtualbox" do |vb|
        vb.name = "server1-centos" # имя виртуальной машины в гепервизоре
        vb.memory = "1024" # RAM
    end
    
    cnt.vm.hostname = "server1-centos" # имя виртуальной машины в системе
    cnt.vm.network "private_network", ip: "192.168.56.150" # настройки сети
    cnt.vm.synced_folder ".", "/vagrant",  # Каталог с хоста синхронизирован в ВМ в /vagrant
          type: "rsync",
          rsync_auto: "true",
          rsync_exclude: [".git/",".vagrant/",".gitignore","Vagrantfile"]
    end

  # Ubuntu
    config.vm.define "server2-ubuntu" do |ubnt|
        ubnt.vm.box = 'ubuntu/trusty64' 
    ubnt.vm.provider "virtualbox" do |vbc|
      # имя виртуальной машины в гепервизоре
      vbc.name = "server2-ubuntu"
      # RAM
      vbc.memory = "1024"
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
  cat /vagrant/vagrant-key.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL

    end
end