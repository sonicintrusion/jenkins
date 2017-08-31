# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "master", primary: true do |master|
    master.vm.box = "bento/centos-7.2"
    master.vm.hostname = "master.jenkins"
    master.vm.boot_timeout = 300
    master.vm.network "forwarded_port", guest: 8080, host: 8888
    master.vm.network "forwarded_port", guest: 80, host: 8080
    #master.vm.network "private_network", ip: "192.168.50.4", :adapter => 2, virtualbox__inet: true
    ##private network doesn't work because the default route is changed and interrupts the provision process
    master.vm.synced_folder "./Downloads", "/downloads"
  end
  config.vm.define "slave" do |slave|
    slave.vm.box = "bento/centos-7.2"
    slave.vm.hostname = "slave.jenkins"
    slave.vm.boot_timeout = 300
    slave.vm.network "forwarded_port", guest: 8080, host: 8800
    #slave.vm.network "private_network", ip: "192.168.50.5", :adapter => 2, virtualbox__inet: true
    slave.vm.synced_folder "./Downloads", "/downloads"
  end
end
