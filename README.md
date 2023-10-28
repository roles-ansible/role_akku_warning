[![Ansible Galaxy](https://raw.githubusercontent.com/roles-ansible/role_akku_warning/master/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/do1jlr/akku_warning)
[![MIT License](https://raw.githubusercontent.com/roles-ansible/role_akku_warning/master/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/role_akku_warning/blob/master/LICENSE)

ansible role: akku warning
==========================

# rewrite in progress!!!
```
cronjob is going to be removed!
systemd timer intruduces
variables may change!

TODO: Verhalten bei akku losen geräten verbessern!
```


This ansible role installs a bash script (per cronjob) which is executed every 3 minutes. This bash script checks if the battery level is below 25 percent and is currently not charging. If this is the case, the program [zenity](https://de.wikipedia.org/wiki/Zenity) installed by this role will generate a popup message stating that the battery is low.
While the battery level is between 15 and 10 percent, it will also attempt to play a sound. But this does not (yet) work reliably.

This role is tested with the [i3 - improved tiling wm](https://i3wm.org/), installed by [this role](https://github.com/chaos-bodensee/role-i3wm.git) at Archlinux, but probably will work on all window magers and the most operating systems!

 Installation and Usage
------------------------

### install with galaxy:
```bash
ansible-galaxy install do1jlr.akku_warning
```

You can execute the role **directly via ansible ad-hoc commands**, but it is highly recomended to create a ansible playbook
```bash
# example ad-hoc command
ansible -m include_role -a "name=do1jlr.akku_warning" localhost
```

### example playbook with galaxy
```yaml
---
- hosts:
  roles:
    - do1jlr.akku_warning
```

### installation via git
```bash
# download this role into your roles directory
git clone https://github.com/roles-ansible/role_akku_warning.git
```

### example playbook
```yaml
---
- name: install akku_warning
  hosts: localhost
  tags:
   - akku_warning
  roles:
    - role_akku_warning
  vars:
    submodules_versioncheck: true
```

 Variables:
-----------
```yaml
---
# simple version check for this playbook
# true is highly recomended
submodules_versioncheck: false

# which user are we currently using?
akku_user: "{{ ansible_user_id }}"

# which sound should we play?
akku_sound_src: 'files/low_battery.m4a'
akku_sound_dest: '/opt/low_battery.m4a'

# should we install cronie?
install_and_enable_cronie: true

# play a video in the background with sound
multimedia_akku_warning: true

# you want to install missing packages?
manage_packages_akku_warning: true
```


 Contribution
------------
If you are missing some features or have an idea for improving this role, please feel free to open an issue - or even better - create a pull request.
