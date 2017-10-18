Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  
  config.vm.provision "shell", inline: <<-SHELL
    sudo -E apt-get -y update
	sudo -E apt-get -y upgrade
    sudo -E apt-get -y install python2.7 python-pip python-dev git libssl-dev libffi-dev build-essential gdb
	sudo pip install --upgrade pip
	sudo pip install --upgrade pwntools --no-cache-dir
	python -c "from pwn import *; context(arch = 'i386', os = 'linux'); print shellcraft.sh()"
	
	sudo dpkg --add-architecture i386
	sudo -E apt-get -y update
	sudo -E apt-get -y install libc6:i386 libncurses5:i386 libstdc++6:i386
  SHELL
end
