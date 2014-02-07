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
  
  config.vm.synced_folder ".", "/home/vagrant"

  # Set the Timezone to something useful
  config.vm.provision :shell, :inline => "echo \"Europe/Paris\" | sudo tee /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata"

  
  config.vm.provision :shell do |shell|
    id_rsa_ssh_key = File.read(File.join(Dir.home, ".ssh", "id_rsa"))
    id_rsa_ssh_key_pub = File.read(File.join(Dir.home, ".ssh", "id_rsa.pub"))
    shell.inline = "echo 'Copying local id_rsa SSH Key to VM for git and auth purposes (login included)...' && echo '#{id_rsa_ssh_key }' > /home/vagrant/.ssh/id_rsa && chmod 0600 /home/vagrant/.ssh/id_rsa"
    shell.inline = "echo 'Copying local id_rsa SSH Key to VM auth_keys for auth purposes (login into VM included)...' && echo '#{id_rsa_ssh_key_pub }' > /home/vagrant/.ssh/authorized_keys && chmod 0600 /home/vagrant/.ssh/authorized_keys"
  end


  
  #config.ssh.private_key_path = [ '~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa' ]
  config.ssh.username = "vagrant"
  config.ssh.forward_agent = true


  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.

  config.vm.network :private_network, ip: "192.168.3.4"

  
end
