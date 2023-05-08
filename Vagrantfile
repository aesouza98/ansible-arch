# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "archlinux/archlinux"
  # config.vm.network "private_network", ip: "192.168.124.151"
  config.vm.provision "shell", inline: "sudo pacman -Sy python2 zsh --noconfirm"
end