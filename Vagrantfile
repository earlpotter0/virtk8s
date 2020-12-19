
NETWORK="10.5.2.12"
MEMORY="4096"
CPUS="2"


Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision :shell, path: "bootstrap.sh"
  config.vm.disk :disk, size: "40GB", primary: true
  config.vm.provider "virtualbox" do |v|
    v.memory = "#{MEMORY}"
    v.cpus = "#{CPUS}"
  end

  config.vm.define "master" do |master|
    master.vm.hostname = "c1-master1"
    master.vm.network "private_network", ip: "#{NETWORK}0"
  end

  (1..3).each do |i|
    config.vm.define "node-#{i}" do |node|
      node.vm.hostname = "c1-node#{i}"
      node.vm.network "private_network", ip: "#{NETWORK}#{i}"
    end
  end
end
