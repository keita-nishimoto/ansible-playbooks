# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "mvbcoding/awslinux"
  config.ssh.insert_key = false
  config.vm.boot_timeout = 120
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provision "network-restart", type: "shell", run: "always", inline: "sudo service network restart"
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "2", "--ioapic", "on", "--cableconnected1", "on"]
  end

  %w(
    laravel-api-sample
    ojt-php
  ).each do |dir|
    config.vm.synced_folder "../#{dir}", "/home/vagrant/#{dir}", mount_options: ["dmode=777","fmode=777"] if  File.exist?("../#{dir}")
  end

  config.vm.provision "ansible" do |ansible|
    ansible.limit = "all"
    ansible.inventory_path = "hosts/local"
    ansible.playbook = "all-servers.yml"
  end
end
