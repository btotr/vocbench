Vagrant.require_version ">= 1.7.0"

$script = <<-SCRIPT
echo installing ansible
apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
apt-get update
apt-get --assume-yes install duplicity python-pip
pip install paramiko
apt-get --assume-yes install ansible
SCRIPT

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false

  config.vm.define :provisioner do |pv|
    pv.vm.hostname = "provisioner"
    pv.vm.network :private_network, ip: '10.0.0.10'
    pv.vm.synced_folder "provisioning/", "/home/vagrant"
    pv.vm.provision "shell", inline: $script
  end

  config.vm.define :vocbench do |vb|
    vb.vm.network :private_network, ip: '10.0.0.11'
  end

  config.vm.define :graphdb do |gd|
    gd.vm.network :private_network, ip: '10.0.0.13'
    gd.vm.provider "virtualbox" do |v|
      v.memory = 2048
    end
  end


end
