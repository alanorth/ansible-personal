# Ansible Playbook

Ansible playbook for base and initial configuration of web server hosting my personal websites.  After successful execution of this playbook, however, there is still some manual work to import databases, copy site content, etc.

## Assumptions
Before you can run this, a few things are assumed:

- You have a clean, minimal Ubuntu 14.04 host up and running
- You have a user account with password-less SSH access to the machine
- You have sudo privileges on the remote host
- You have created a `hosts` file with something like:

```ini
[web]
web01
```

## Use
Once you've satisfied the the above assumptions, you can execute:

    $ ansible-playbook web.yml -i hosts -K

## Testing in a VM (KVM)
A simple way to test locally in a virtual machine using libvirt + KVM:

    $ sudo virt-install -n web01 -r 1024 --vcpus 2 \
    -l http://ubuntu.mirror.ac.ke/ubuntu/dists/trusty/main/installer-amd64/ \
    --os-type=linux --os-variant=ubuntusaucy \
    --disk /var/lib/libvirt/images/web01.qcow2,device=disk,bus=virtio,format=qcow2,size=40 \
    --vnc --cpuset=1,2 -x "auto=true priority=critical url=https://help.ubuntu.com/lts/installation-guide/example-preseed.txt"

This boots from a network Ubuntu mirror, then uses a preseed to automate the OS installation.

## Testing in Vagrant
Not as simple as on GNU/Linux with KVM, but still easy:

    $ vagrant up

A new VirtualBox VM will come up with the IP `192.168.33.10`.

## License
Copyright (C) 2014 - 2015 Alan Orth

The contents of this repository are free software: you can redistribute
it and/or modify it under the terms of the GNU General Public License
as published by the Free Software Foundation, either version 3 of the
License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
