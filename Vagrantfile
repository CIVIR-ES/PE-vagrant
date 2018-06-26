Vagrant.configure(2) do |config|
  config.vm.box_check_update = false
  config.vm.define "master" do |master|
    master.vm.box = "bento/centos-7.3"
    master.vm.hostname = "master.vagrant.test"
    master.vm.network :private_network, ip: "10.10.10.10"
    master.vm.network :public_network
    master.vm.provider "virtualbox" do |v|
      v.memory = 3072
      v.cpus = 4
    end
    master.vm.provision "shell", inline: <<-SHELL
      mkdir -p /opt/puppetlabs/server/apps
      /vagrant/files/puppet-enterprise-2016.4.2-el-7-x86_64/puppet-enterprise-installer -c /vagrant/files/pe.conf
      /opt/puppetlabs/puppet/bin/puppet agent -t
    SHELL
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "bento/centos-7.3"
    node1.vm.hostname = "node1.vagrant.test"
    node1.vm.network :private_network, ip: "10.10.10.15"
    node1.vm.network :public_network
    node1.vm.provision "shell", inline: <<-SHELL
      echo "10.10.10.10    master.vagrant.test    master" >> /etc/hosts
#     echo "192.168.0.28	master.vagrant.test    master" >> /etc/hosts
      curl -k https://master:8140/packages/current/install.bash | sudo bash
    SHELL
  end
end
