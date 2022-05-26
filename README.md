# ansible-arch

Ansible collection of Playbook and Roles (+ vars), focused on automatically deploy my work laptop.
Automatically installs every package that I need, configure some stuff and make everything run smoothly based on my preferences.

## Roles

* Core: performs the basic steps on a fresh OS
    * hostname setting
    * user creation and configuration
    * timezone, locale and keymapping configuration
    * pacman configuration, mirror refresh, reflector install and mirror sort
    * basic packages install
    * populates home with a directories skel
* Desktop:
    * Install the selected DE, if the `installde` variable is set to `True`
    * Installs every 'extra' package based on DE (gnome-tweaks on gnome or touche (+libinput-gestures) on plasma, for example)
* Packages:
    * Every other package is installed/configured by this role.

## Plan
To come:
* Automatically restore dotfiles and backup (manual for now)

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
* Open `group_vars/all` and set the variables. 
   * user: User definitions
   * upassword: User's password
   * hostname: Set the machine hostname to this value
   * desktop: Use `plasma` or `gnome` to select the desired DE
   * installde: Use `True` or `False` to let Ansible know if it needs to install the Desktop Environment
   * pkg_core: Core pacman packages
   * aur_core: Core AUR packages
   * desktop_core: Core xorg packages
   * plasma: KDE's default packages (ignored if using gnome)
   * pkg_plasma: Extra plasma pacman packages
   * aur_plasma: Extra plasma AUR packages
   * gnome: GNOME's main packages
   * pkg_gnome: Extra GNOME packages
   * aur_gnome: Extra AUR GNOME packages
   * fpk_gnome: Extra GNOME flatpaks
   * pkg_util: Utilities and general packages
   * pkg_other: Nonessential packages 
   * pkg_extra: Programs that are going to be installed with pacman
   * aur_pkg: General AUR packages
   * flatpak: General Flatpaks
* Run `ansible-playbook playbook.yml -i hosts.ini -l localhost` to provision your Arch Linux

Every roles is tagged. You can run individual Roles [using them](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html).
