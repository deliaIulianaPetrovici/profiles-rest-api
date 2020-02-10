# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
 # The most common configuration options are documented and commented below.
 # For a complete reference, please see the online documentation at
 # https://docs.vagrantup.com.

 # Every Vagrant development environment requires a box. You can search for
 # boxes at https://vagrantcloud.com/search.
 config.vm.box = "ubuntu/bionic64"
 #pend it to a specific version to avoid any chnages or updates being made to this image breking the steps in the course
 config.vm.box_version = "~> 20191107.0.0"

#it maps a port from our local machine to the machine on our server
#by default ports are not automatically accesable on anyy guest machine so u need to add this line so we can access them
 config.vm.network "forwarded_port", guest: 8000, host: 8000

#this is how u can run scripts when u create your server
 config.vm.provision "shell", inline: <<-SHELL
 #disable the auto update which conflicts with the down below update
   systemctl disable apt-daily.service
   systemctl disable apt-daily.timer

#update line which updates the local repositry with all the available packages to we can install python3 virtual environment
   sudo apt-get update
   sudo apt-get install -y python3-venv zip
   touch /home/vagrant/.bash_aliases
   if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
     echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
     echo "alias python='python3'" >> /home/vagrant/.bash_aliases
   fi
 SHELL
end
