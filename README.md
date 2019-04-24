 Akku Warning role
---------------------

This ansible warning will install an bash Script, that will be executet every 3 minutes.

If your batterie is under 25 min, it will make a warning.

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

