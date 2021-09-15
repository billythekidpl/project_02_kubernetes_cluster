# -*- mode: ruby -*-
# vi: set ft=ruby :
VM_BOX = "bento/ubuntu-18.04"

Vagrant.configure("2") do |config|
  # provisioner configuration
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--cpus", "1"]

  end
  
  # provisioning and configuring master-node
  config.vm.define "master-node" do |master|
    master.vm.box = VM_BOX
  end

  # provisioning and configuring worker-node1
  config.vm.define "worker-node-1" do |worker1|
    worker1.vm.box = VM_BOX
  end
end
