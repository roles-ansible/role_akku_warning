[![Ansible Galaxy](https://raw.githubusercontent.com/roles-ansible/role_akku_warning/master/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/do1jlr/akku_warning) [![Build Status](https://travis-ci.org/roles-ansible/role_akku_warning.svg?branch=master)](https://travis-ci.org/roles-ansible/role_akku_warning) [![MIT License](https://raw.githubusercontent.com/roles-ansible/role_akku_warning/master/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/role_akku_warning/blob/master/LICENSE)

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


 Missing something?
----------------
Please feel free to open a [github](https://github.com/roles-ansible/role_akku_warning.git) Issue or Pull-Request. Thanks <3

 Testing
----------
This role is tested with [these github-action](https://github.com/search?q=topic%3Acheck-ansible+topic%3Agithub-actions+org%3Aroles-ansible&type=Repositories) tests for different versions of differen linux systems. Linting is tested via travis-ci and the  [ansible-lint action](https://github.com/marketplace/actions/ansible-lint).
If you want to find out more about our tests, please have a look at the github marketplace.

| test status | Github Marketplace |
| :---------  | :----------------  |
| [![Travis Build Status](https://travis-ci.org/roles-ansible/role_akku_warning.svg?branch=master)](https://travis-ci.org/roles-ansible/role_akku_warning) | [.travis.yml](https://github.com/roles-ansible/role_akku_warning/blob/master/.travis.yml) |
|||
| [![Ansible Lint check](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20Lint%20check/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+Lint+check%22) | [ansible-lint action](https://github.com/marketplace/actions/ansible-lint)
| [![Ansible check debian:stable](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:stable/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Astable%22) | [ansible test with debian stable](https://github.com/marketplace/actions/check-ansible-debian-stable) |
| [![Ansible check debian:latest](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:latest/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Alatest%22) | [ansible test with debian latest](https://github.com/marketplace/actions/check-ansible-debian-latest) |
| [![Ansible check debian:sid](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:sid/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Asid%22) | [ansible test with debian sid](https://github.com/marketplace/actions/check-ansible-debian-sid) |
| [![Ansible check debian:buster](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:buster/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Abuster%22) | [ansible test with debian buster](https://github.com/marketplace/actions/check-ansible-debian-buster) |
| [![Ansible check debian:jessie](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:jessie/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Ajessie%22) | [ansible test with debian jessie](https://github.com/marketplace/actions/check-ansible-debian-jessie) |
| [![Ansible check debian:stretch](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:stretch/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Astretch%22) | [ansible test with debian stretch](https://github.com/marketplace/actions/check-ansible-debian-stretch) |
| | |
| [![Ansible check archlinux:latest](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20archlinux:latest/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+archlinux%3Alatest%22) | [ansible test with archlinux latest](https://github.com/marketplace/actions/check-ansible-archlinux-latest) |
| | |
| [![Ansible check ubuntu:latest](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:latest/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Alatest%22) | [ansible test with ubuntu latest](https://github.com/marketplace/actions/check-ansible-ubuntu-latest) |
| [![Ansible check ubuntu:bionic](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:bionic/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Abionic%22) | [ansible test with ubuntu bionic](https://github.com/marketplace/actions/check-ansible-ubuntu-bionic) |
| [![Ansible check ubuntu:eoan](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:eoan/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Aeoan%22) | [ansible test with ubuntu eoan](https://github.com/marketplace/actions/check-ansible-ubuntu-eoan) |
| [![Ansible check ubuntu:trusty](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:trusty/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Atrusty%22) | [ansible test with ubuntu trusty](https://github.com/marketplace/actions/check-ansible-ubuntu-trusty) |
| [![Ansible check ubuntu:xenial](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:xenial/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Axenial%22) | [ansible test with ubuntu xenial](https://github.com/marketplace/actions/check-ansible-ubuntu-xenial) |

 Contribution
------------
If you are missing some features or have an idea for improving this role, please feel free to open an issue - or even better - create a pull request.
