# Add new user. -m flag creates home directory. -s passes shell
- useradd -m -g users -G wheel -s /bin/bash username # perhaps not use -G wheel
- passwd

# Enable sudo use for wheel members
- visudo uncomment wheel ALL=(ALL) ALL
(opens in vi probably: use :wq to save and exit

-Only on 32bit systems:  Uncomment multilib in (/etc/pacman.conf) or multilib-testing for 32-bit apps

- install yaourt
- maybe add correct mirrorlist for your country in pacman (/etc/pacman.d/mirrorlist)
- install sudo (pacman -S sudo)

# Install i3 window manager

- pacman -S i3 (install all packages), see i3wm.txt for more info

