 Akku Warning role
---------------------

This ansible warning will install an bash Script, that will be executet every 3 minutes.

If your akku is under 25 min, it will make a warning.

 Variables:
-----------
```
# should we install cronie?
install_and_enable_cronie: false

# play a video in the background with sound
multimedia_akku_warning: true
```

