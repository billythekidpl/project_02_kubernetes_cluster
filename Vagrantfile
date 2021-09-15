# -*- mode: ruby -*-
# vi: set ft=ruby :
VM_BOX = "bento/ubuntu-18.04"
MASTER_MEM = 2048
MASTER_CPU = "2"
WORKER_MEM = 1024
WORKER_CPU = "1"

Vagrant.configure("2") do |config|
  # provisioner configuration
  #config.vm.provider "virtualbox" do |vb|
  #  vb.memory = MASTER_MEM
  #  vb.customize ["modifyvm", :id, "--cpus", MASTER_CPU]
  #
  #end
  
  # provisioning and configuring master-node
  config.vm.define "master-node" do |master|
    master.vm.box = VM_BOX
    master.vm.provider "virtualbox" do |vb|
      vb.memory = MASTER_MEM
      vb.customize ["modifyvm", :id, "--cpus", MASTER_CPU]
      vb.name = "master-node"
    end
  end

  # provisioning and configuring worker-node1
  config.vm.define "worker-node-1" do |worker1|
    worker1.vm.box = VM_BOX
    worker1.vm.provider "virtualbox" do |vb|
      vb.memory = WORKER_MEM
      vb.customize ["modifyvm", :id, "--cpus", WORKER_CPU]
      vb.name = "worker-node"
    end
  end
end
