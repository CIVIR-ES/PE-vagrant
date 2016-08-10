Vagrant.configure(2) do |config|
<<<<<<< HEAD
  config.vm.define "master1" do |master1|

    master1.vm.box = "centos/7"
    master1.vm.hostname = "master1"
    master1.vm.network "public_network", use_dhcp_assigned_default_route: true, ip: "192.168.0.164", bridge: "wlo1"
    master1.vm.network "forwarded_port", guest: 443, host: 22102
  
    master1.vm.provider "virtualbox" do |v|
      v.memory = 2048
  #   v.cpus = 2
    end
    master1.vm.provision :file do |f|
      f.source = "files/master1"
      f.destination = "/tmp/"
    end
  
  # master1.vm.provision "shell", inline: <<-SHELL
  ## Uncomment to download installer
  # curl https://s3.amazonaws.com/pe-builds/released/2016.2.0/puppet-enterprise-2016.2.0-el-7-x86_64.tar.gz -o /tmp/files/  puppet-enterprise-2016.2.0-el-7-x86_64.tar.gz
    #SHELL
    
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
#      sudo /opt/puppetlabs/bin/puppet agent -t
    SHELL

  end



=======
  config.vm.box = "centos/7"
  config.vm.hostname = "master1"
  config.vm.network :forwarded_port, guest: 3000, host: 8080
# config.vm.network :private_network, ip: "192.168.68.8"
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
#   v.cpus = 2
  end
  config.vm.provision :file do |f|
    f.source = "files"
    f.destination = "/tmp/"
  end

#config.vm.provision "shell", inline: <<-SHELL
#!  sudo yum -y update
# cd /tmp/files
# sudo mkdir -p /opt/puppetlabs/server/apps
# sudo mv /tmp/files/hosts /etc/
#dependencies puppet master START
# sudo yum -y install pciutils
# sudo yum -y install system-logos
# sudo yum -y install which
# sudo yum -y install libxml2
# sudo yum -y install dmidecode
# sudo yum -y install net-tools
# sudo yum -y install curl
# sudo yum -y install mailcap
# sudo yum -y install libjpeg
# sudo yum -y install libtool-ltdl
# sudo yum -y install unixODBC
# sudo yum -y install libxslt
# sudo yum -y install zlib
#dependencies puppet master END
# tar xfz puppet-enterprise-2016.2.0-el-7-x86_64.tar.gz
# sudo /tmp/files/puppet-enterprise-2016.2.0-el-7-x86_64/puppet-enterprise-installer -c /tmp/files/pe.conf
# sudo puppet agent -t
  
config.vm.provision "shell", path: "scripts/pre-install.sh"
config.vm.provision "shell", path: "scripts/install.sh"
  
#SHELL
>>>>>>> 8281b5eb06fd041408236ed0b4a748d3e5154979
end
