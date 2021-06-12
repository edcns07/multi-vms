# -*- mode: ruby -*-
# vi: set ft=ruby :

#Vagrantfile API/syntax version. Dont touch unless you know what you're doing 
 Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7"
  config.vm.box_check_update = false
  
  config.vm.provision "file", source: "~/projects/vagrant/files/git-config", destination: "~/.gitconfig"
  config.vm.provision "shell", path: "https://raw.githubusercontent.com/edcns07/vagrant/master/scripts/centos7.9-common.sh"
  
  config.vm.define "web" do |web|
     web.vm.hostname = "web-server"
     web.vm.network "forwarded_port", guest: 80, host: 8080  
     web.vm.network "private_network", ip: "192.168.10.2"
     web.vm.provision "shell", path: "https://raw.githubusercontent.com/edcns07/vagrant/master/scripts/centos7.9-web.sh"
  end   
  config.vm.define "db" do |db|
    db.vm.hostname = "db-server"
    db.vm.network "private_network", ip: "192.168.10.3"
    db.vm.provision "shell", path: "https://raw.githubusercontent.com/edcns07/vagrant/master/scripts/centos7.9-db.sh"
  end

end

