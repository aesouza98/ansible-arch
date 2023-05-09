# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider "libvirt" do |v|
    v.memory = 2048
    v.cpus = 2
  end
  config.vm.box = "archlinux/archlinux"
  config.vm.synced_folder ".", "/vagrant", disabled: "true"
  config.vm.provision "shell", inline: "sudo pacman -Sy git ansible --noconfirm"
end
