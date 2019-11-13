# vagrant init ubuntu/bionic64
Vagrant.configure("2") do |config|

    config.vm.provider "virtualbox" do |vb|
     vb.memory = 1024
     vb.cpus = 2
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
     vb.provision "file", source: "template/hosts", destination: "/etc/hosts" 
   end
   # This is the first virtual machine represesnting the load balancer
   config.vm.define "loadbalancer01.al.local" do |subconfig|
     subconfig.vm.box = "ubuntu/bionic64"
     subconfig.vm.hostname = "loadbalancer01.al.local"
     subconfig.vm.network :private_network, ip: "10.0.0.13"
     subconfig.vm.provision "shell", inline: <<- LOADBALANCERONE
       sudo apt-get -y update
       sudo apt-get -y install gcc make
       sudo apt-get -y install software-properties-common
       sudo apt-add-repository ppa:ansible/ansible
       sudo apt-get -y install ansible
       sudo firewall-cmd --add-service=http --permanent
       sudo firewall-cmd --reload
     LOADBALANCERON 
   end

   # This is the 2nd virtual machine representing first nginx webserver  

   config.vm.define "webserver01.al.local" do |subconfig|
    subconfig.vm.box = "ubuntu/bionic64"
    subconfig.vm.hostname = "webserver01.al.local"
    subconfig.vm.network :private_network, ip: "10.0.0.14"
    subconfig.vm.provision "shell", inline: <<- WEBSERVERONE
      sudo apt-get -y update
      sudo apt-get -y install gcc make
      sudo apt-get -y install software-properties-common
      sudo apt-add-repository ppa:ansible/ansible
      sudo apt-get -y install ansible
      sudo firewall-cmd --add-service=http --permanent
      sudo firewall-cmd --reload
     WEBSERVERONE
   end

   # This is the 3rd virtual machine representing second nginx webserver

   config.vm.define "webserver02.al.local" do |subconfig|
    subconfig.vm.box = "ubuntu/bionic64"
    subconfig.vm.hostname = "webserver02.al.local"
    subconfig.vm.network :private_network, ip: "10.0.0.15"
    subconfig.vm.provision "shell", inline: <<- WEBSERVERTWO
      sudo apt-get -y update
      sudo apt-get -y install gcc make
      sudo apt-get -y install software-properties-common
      sudo apt-add-repository ppa:ansible/ansible
      sudo apt-get -y install ansible
      sudo firewall-cmd --add-service=http --permanent
      sudo firewall-cmd --reload
     WEBSERVERTWO
   end   
  
end