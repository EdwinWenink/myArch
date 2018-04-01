# Adjusting resolution

* Check framebuffer with hwinfo --framebuffer (I did not get this to work)
* If GRUB is used, edit /etc/default/grub: GRUB_CMDLINE_LINUX_DEFAULT="quiet video="1360x768" (or any other supported resolution.
* Adjust size of Grub loader itself with: GRUB_GFXMODE="1360x768x24"
* Run grub-mkconfig -o /boot/grub/grub.cfg to activate the configuration
