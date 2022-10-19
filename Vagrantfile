# create a virtual machine using vagrant
# virtual box
# vagrant
# ruby - dev-kit
# test the installation
# vagrant
# ruby --version

# creating a vm with linux os using ubuntu 16.04LTS

Vagrant.configure("2") do |config|
#

 config.vm.box = "ubuntu/xenial64"  
# creating a virtual machine ubuntu
 config.vm.network "private_network", ip: "192.168.56.12"

 config.vm.synced_folder ".", "/home/vagrant/app", create: true
 # config.vm.synced_folder "environment/", "/srv/environment", create: true 
 config.vm.provision "shell", path: "provision.sh"



end

