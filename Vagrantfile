# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::configure("2") do |config|
  
  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--memory", "1536",
      "--cpus", "2",
      "--ioapic", "on"
      ]
    end

  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.hostname = "devbox"
  
  config.vm.synced_folder ".", "/home/vagrant/mezzanine/project", { 
    :mount_options   => ['dmode=777,fmode=777'] 
  }

  # Set the Timezone to something useful
  config.vm.provision :shell, :inline => "echo \"Europe/Paris\" | sudo tee /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata"

  config.vm.provision :shell, :inline => "echo -e '#{File.read("#{Dir.home}/.gitconfig")}' > '/home/vagrant/.gitconfig'"
  config.vm.provision :shell, :inline => "echo -e '#{File.read("#{Dir.home}/.ssh/id_rsa")}' > '/home/vagrant/.ssh/id_rsa'"
  config.vm.provision :shell, :inline => "echo -e '#{File.read("#{Dir.home}/.ssh/id_rsa.pub")}' > '/home/vagrant/.ssh/id_rsa.pub'"

  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.

  config.vm.network :private_network, ip: "192.168.3.3"

  
end
