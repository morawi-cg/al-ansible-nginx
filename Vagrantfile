Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |vb|
   vb.memory = 1024
   vb.cpus = 2
   vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]

 end
 config.vm.define "loadbalancer01.al.local" do |subconfig|
   subconfig.vm.box = "ubuntu/bionic64"
   subconfig.vm.hostname = "loadbalancer01.al.local"
   subconfig.vm.network :private_network, ip: "10.0.0.13"
 end

 config.vm.define "webserver01.al.local" do |subconfig|
   subconfig.vm.box = "ubuntu/bionic64"
   subconfig.vm.hostname = "webserver01.al.local"
   subconfig.vm.network :private_network, ip: "10.0.0.14"

 end

 config.vm.define "webserver02.al.local" do |subconfig|
   subconfig.vm.box = "ubuntu/bionic64"
   subconfig.vm.hostname = "webserver02.al.local"
   subconfig.vm.network :private_network, ip: "10.0.0.15"
 end

 # Install shared components on all machines  
    
 config.vm.provision "shell", inline: <<-SHELL   
  sudo apt-get -y update
  sudo apt-get -y install gcc make
  sudo apt-add-repository ppa:ansible/ansible
  sudo apt-get -y install ansible
  sudo apt-get -y install  apt-transport-https ca-certificates curl software-properties-common
  sudo echo "10.0.0.13       loadbalancer01.al.local" >> /etc/hosts
  sudo echo "10.0.0.14       webserver01.al.local"  >> /etc/hosts
  sudo echo "10.0.0.15       webserver02.al.local"  >> /etc/hosts
 SHELL
 config.vm.provider :virtualbox do |vb|
 vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
end
end
