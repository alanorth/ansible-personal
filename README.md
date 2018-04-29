# Ansible Playbook
Ansible playbook for base and initial configuration of the web server hosting my personal websites. After successful execution of this playbook, however, there is still some manual work to import databases, copy site content, etc.

## Assumptions
Before you can run this, a few things are assumed:

- You have a clean, minimal Debian 9, Ubuntu 16.04, or Ubuntu 18.04 host up and running
- You have a user account with password-less SSH access to the machine
- You have sudo privileges on the remote host
- You have created a `hosts` file with something like:

```ini
[web]
web01
```

## Use
Once you've satisfied the the above assumptions, you can execute:

    $ ansible-playbook web.yml

## Todo

- Update packages for Ubuntu 18.04 (mariadb, nginx, tarsnap currently using packages for 17.10 artful)
- Switch from `cron-apt` to [`unattended-upgrades`](https://wiki.debian.org/UnattendedUpgrades)

## License
Copyright (C) 2014 - 2018 Alan Orth

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
