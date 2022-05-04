# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
    v.customize ["modifyvm", :id, "--vram", "128"]
  end
  config.vm.box = "archlinux/archlinux"
  config.vm.network "private_network", ip: "192.168.56.2"
  config.vm.provision "shell", inline: "sudo pacman -Sy python2 zsh --noconfirm"
end
