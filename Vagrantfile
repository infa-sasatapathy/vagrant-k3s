Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64" # Ubuntu 22.04

  # Common configurations for all machines
  config.vm.provision "shell", inline: <<-SHELL
    # Fix DNS resolution
    echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
    echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf > /dev/null
	
  SHELL

  # Master node
  config.vm.define "k3s-master" do |master|
    master.vm.hostname = "k3s-master"
    master.vm.network "private_network", ip: "192.168.56.101"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end

  # Worker node 1
  config.vm.define "k3s-worker1" do |worker1|
    worker1.vm.hostname = "k3s-worker1"
    worker1.vm.network "private_network", ip: "192.168.56.102"
    worker1.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 2
    end
  end

  # Worker node 2
  config.vm.define "k3s-worker2" do |worker2|
    worker2.vm.hostname = "k3s-worker2"
    worker2.vm.network "private_network", ip: "192.168.56.103"
    worker2.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 2
    end
  end
end
