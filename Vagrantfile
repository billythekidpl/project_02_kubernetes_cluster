# Variables
VM_BOX = "bento/ubuntu-18.04"
MASTER_MEM = 2048
MASTER_CPU = "2"
WORKER_MEM = 1024
WORKER_CPU = "1"
WORKERS_QUANTITY = 3

Vagrant.configure("2") do |config|
  
  #checking if host machine is using Wondows. If so, change provisioning method to ansible_local
  provisioner = Vagrant::Util::Platform.windows? ? :ansible_local : :ansible
  config.ssh.insert_key = false

  # provisioning and configuration of master-node
  config.vm.define "master-node" do |master|
    master.vm.box = VM_BOX
    master.vm.provider "virtualbox" do |vb|
      vb.memory = MASTER_MEM
      vb.customize ["modifyvm", :id, "--cpus", MASTER_CPU]
      vb.name = "master-node"
    end
    master.vm.network "private_network", ip: "19.0.0.10"
    master.vm.hostname = "master-node"
    # using Ansible to configure master-node
    master.vm.provision provisioner do |ansible|
      ansible.playbook = "conf-playbooks/master-node.yaml"
      ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
    end
  end

  # provisioning and configuration of worker-nodes
  (1..WORKERS_QUANTITY).each do |i|
    config.vm.define "worker-node-#{i}" do |worker|
      worker.vm.box = VM_BOX
      worker.vm.provider "virtualbox" do |vb|
        vb.memory = WORKER_MEM
        vb.customize ["modifyvm", :id, "--cpus", WORKER_CPU]
        vb.name = "worker-node-#{i}"
      end
      worker.vm.network "private_network", ip: "19.0.0.#{i+10}"
      worker.vm.hostname = "worker-node-#{i}"
      # using Ansible to configure master-node
      worker.vm.provision provisioner do |ansible|
        ansible.playbook = "conf-playbooks/worker-node.yaml"
        ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
      end
    end
  end
end
