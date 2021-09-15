# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # provisioner configuration
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--cpus", "1"]

  end
  
  # provisioning and configuring master-node
  config.vm.define "master-node" do |master|
    master.vm.box = "bento/ubuntu-18.04"
  end

  # provisioning and configuring worker-node1
  config.vm.define "worker-node-1" do |worker1|
    worker1.vm.box = "bento/ubuntu-18.04"
  end
end
