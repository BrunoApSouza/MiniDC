# -*- mode: ruby -*-
# vi: set ft=ruby :

#vm dabase
Vagrant.configure("2") do |config|
    config.vm.define "db" do |db|
    db.vm.box = "ubuntu/bionic64"
    db.vm.hostname = "MiniDc-Database"
    db.vm.network "private_network", ip: "172.17.177.21"

    db.vm.provider "virtualbox" do |v|
     v.name = "MiniDC-DataBase"
     v.memory = 512
     v.cpus = 1
    end
  end
  #vm Blog
  config.vm.define "blog" do |blog|
    blog.vm.box = "ubuntu/bionic64"
    blog.vm.hostname = "MiniDC-Blog"
    blog.vm.network "private_network", ip: "172.17.177.22"

    blog.vm.provider "virtualbox" do |v|
     v.name = "MiniDC-Blog"
     v.memory = 512
     v.cpus = 1
    end
  end
  #vm controller
  config.vm.define "controller" do |controller|
    controller.vm.box = "ubuntu/bionic64"
    controller.vm.hostname = "MiniDC-AnsibleController"
    controller.vm.network "private_network", ip: "172.17.177.11"

    controller.vm.provider "virtualbox" do |v|
     v.name = "MiniDC-AnsibleController"
     v.memory = 512
     v.cpus = 1
    end
  end
end