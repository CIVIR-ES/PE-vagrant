Vagrant.configure(2) do |config|
  config.vm.define "master1" do |master1|
    master1.vm.box = "centos/7"
    master1.vm.hostname = "master1"
    master1.vm.network "public_network", use_dhcp_assigned_default_route: true, ip: "192.168.0.164", bridge: "wlo1"
    master1.vm.network "forwarded_port", guest: 443, host: 22102
    master1.vm.provider "virtualbox" do |v|
      v.memory = 2048
    end
    master1.vm.provision :file do |f|
      f.source = "files/master1"
      f.destination = "/tmp/"
    end
    master1.vm.provision "shell", path: "scripts/pre-install.sh"
    master1.vm.provision "shell", path: "scripts/install.sh"
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "centos/7"
    node1.vm.hostname = "node1"
    node1.vm.network "public_network", use_dhcp_assigned_default_route: true, ip: "192.168.0.165",
bridge: "wlo1"
    node1.vm.provision :file do |f|
      f.source = "files/node1/"
      f.destination = "/tmp/"
    end
    node1.vm.provision "shell", inline: <<-SHELL
      sudo mv /tmp/node1/hosts /etc/hosts
      sudo curl -k https://master1:8140/packages/current/install.bash | sudo bash
#     sudo /opt/puppetlabs/bin/puppet agent -t
    SHELL
  end
end
