# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ## Escolha da Box
  config.vm.box = "ubuntu/bionic64"

  ## DATABASE
  config.vm.define "database" do |db|
    db.vm.network "private_network", ip: "172.17.177.21"
    db.vm.hostname = "MiniDc-Database"

    # Configurações de Size da VM
    db.vm.provider "virtualbox" do |v|
      v.name = "MiniDC-DataBase"
      v.memory = 512
      v.cpus = 1
    end
  end

  ## BLOG
  config.vm.define "blog" do |blog|
    blog.vm.network "private_network", ip: "172.17.177.22"
    blog.vm.hostname = "MiniDC-Blog"

    # Configurações de Size da VM
    blog.vm.provider "virtualbox" do |v|
      v.name = "MiniDC-Blog"
      v.memory = 512
      v.cpus = 1
    end
  end

    ## CONTROLLER
    config.vm.define 'controller' do |controller|
      controller.vm.network "private_network", ip: "172.17.177.11"
      controller.vm.hostname = "MiniDC-AnsibleController"
    
    # restringindo o permissisonamento da pasta vagrant
    controller.vm.synced_folder "./", "/vagrant", mount_options: ["dmode=750,fmode=600"]
    
    # Configurações de Size da VM
    controller.vm.provider "virtualbox" do |v|
      v.name = "MiniDC-AnsibleController"
      v.memory = 512
      v.cpus = 1
    end

    ## Integrando o Ansible no Provisionamento
    controller.vm.provision :ansible_local do |ansible|
      ansible.install_mode = "default"
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "inventory"
      ansible.verbose  = true
      ansible.install  = true
      ansible.limit    = "all"
    end
  end
end
