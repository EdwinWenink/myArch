# Install i3 (or i3-gaps)
pacman -S i3 (installs multiple packages: 1) i3-wm 2) i3blocks 3)i3lock 4) i3status

pacman -S i3-gaps


# Additional packages: 
* dmenu (utily for launching apps) 
* feh (image/wallpaper utility)
* conky (display system info)
* xorg-backlight (probably already installed, adjust laptop screen brightness)
* lxappearance (for GTK-theme customization)

# To boot:

* Install xorg (also installs xorg-server)
	- Test if xorg works by running 'startx'
* Install xorg-xinit
* Add "exec i3" to "xinitrc" in user home directory or /etc/X11/xinit/ and replace default exec's (by default there is e.g. xterm, replace it) 
	- to get xinitrc in home directory use: cp /etc/X11/xinit/xinitrc ~/.xinitrc
* Add to ~/.bash_profile:

	if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then
	startx
	fi
* Make sure that a terminal emulator is installed before autostarting i3. In case of being stuck in i3 without being able to open any terminal, use another ttyN, run as root, and install one.

# Set correct resolution and background
* run xrandr to see information on possible options, as well as connected screen (e.g. VGA-1)
* run feh --bg-scale /path/to/image.png (pay attention to include the *full* path, not ~)

Add the following options to ~/.xinitrc

* Run xrandr --output VGA-1 --mode 1920x1080 
* add "~/.fehbg &" to .xinitrc

# GRUB (adjust kernel paramters for resolution)
* In /etc/default/grub set GRUB_CMDLINE_LINUX_DEFAULT  ="quiet video=1920x1080" or ..."quiet vga=799" (deprecated method for 1600x1200). Check if format is supported.
* To activate new config, run:  grub-mkconfig -o /boot/grub/grub.cfg
* For GRUB itself, set GRUB_GFXMODE to a desired resolution.

# For framebuffer info
* hwinfo --framebuffer --log hwinfo.log (did not work for me without logging) 

# Custom ratios in VirtualBox (on host)
In VirtualBox install folder, run in shell: ./VBoxManage setextradata "Arch Linux  " "CustomVideoModel" "1920x1080x32"

