[![Build Status](https://travis-ci.org/chaos-bodensee/role_akku_warning.svg?branch=master)](https://travis-ci.org/chaos-bodensee/role_akku_warning)
[![MIT License](https://raw.githubusercontent.com/chaos-bodensee/role_akku_warning/master/.github/license.svg?sanitize=true)](https://github.com/chaos-bodensee/role_akku_warning/blob/master/LICENSE)

 Akku Warning role
---------------------
<a href="https://galaxy.ansible.com/do1jlr/akku_warning"><img width="80px" src="https://galaxy.ansible.com/assets/galaxy-logo-02.svg"/></a>

### Get it directly from Ansible Galaxy 
```bash
$ ansible-galaxy install do1jlr.akku_warning
```

### Function

This ansible warning will install an bash Script, that will be executet every 3 minutes.

If your batterie is under 25 percent, it will start warning you.

This role is only tested on arch, but probably will work on all distros!

 Variables:
-----------
```
# Your username you mostly use on your device
akku_user: "{{ ansible_user_id }}"

# should we install cronie?
install_and_enable_cronie: false

# play a video in the background with sound
multimedia_akku_warning: true
```
*For a complete view of all variables pleas have a look into the default folder.*
