# LOCKED FOR NOW
Variables are locked for now, until the development is done and everything is ready to be used.

# ansible-arch

Ansible collection of Playbook and Roles (+ vars), focused on automatically deploy my work laptop.
Automatically installs every package that I need, configure some stuff and make everything run smoothly based on my preferences.

## Roles

* Core: performs the basic steps on a fresh OS
    * hostname setting
    * user creation
    * timezone, locale and keymapping configuration
    * pacman configuration, mirror refresh, reflector install and mirror sort
    * basic packages install
    * populates home with a directories skel
* User: Set the user's configs
    * Shell configuration
    * Home folder skel
    * Etc
* Desktop:
    * Installs the DE that I want to use (plasma or gnome), based on the defined variable.
    * Installs every 'extra' package based on DE (gnome-tweaks on gnome or touche (+libinput-gestures) on plasma, for example)
* Packages:
    * Every other package is installed/configured by this role.

## Plan
To come:
* Automatically restore my dotfiles (manually for now)

## Install
### Clone
```bash
git clone https://github.com/nanoesouza/ansible-arch
```

### Requirements

* Ansible
* Vagrant (otional, to test on a disposable vm)

## Configuration
The configuration of the playbook is done by editing the `host_vars/{ distro }` file, you can mainly edit:

* some settings for the archlinux installation customization
* dotfiles git repo location
* packages list to be installed for the various roles
* User customization
* Password

## Usage
### Vagrant playground
```bash
cd ansible-arch
vagrant up
ansible-playbook -i vagrant.inventory playbook.yml
```

Every roles is tagged. You can run individual Roles [using them](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html).
