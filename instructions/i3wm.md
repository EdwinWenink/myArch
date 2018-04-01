# Install i3 (or i3-gaps)
pacman -S i3 (installs multiple packages: 1) i3-wm 2) i3blocks 3)i3lock 4) i3status


Additional packages: 
5) dmenu (utily for launching apps) 
6) feh (wallpaper utility)
7) conky (display system info)
8) xorg-backlight (probably already installed, adjust laptop screen brightness)
9) lxappearance (for GTK-theme customization)

To boot:

10) Install xorg (also installs xorg-server)
	- Test if xorg works by running 'startx'
11) Install xorg-xinit
12) Add "exec i3" to "xinitrc" in user home directory or /etc/X11/xinit/ and replace default exec's (by default there is e.g. xterm, replace it) 
	- to get xinitrc in home directory use: cp /etc/X11/xinit/xinitrc ~/.xinitrc
13) Add to ~/.bash_profile:

	if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then
	startx
	fi
14) Make sure that a terminal emulator is installed before autostarting i3. In case of being stuck in i3 without being able to open any terminal, use another ttyN, run as root, and install one.
# ADJUST SCREEN RESOLUTION
15) run xrandr with options to see information on possible options, as well as connected screen (e.g. VGA-1)
16) xrandr --output VGA-1 --mode 1920x1080 (I haven't found the best place to run this command so far)

17) install gtk3 (cf. lxappearance), gtk2 etc. (doesn't seem to do shit with lxappearance)
# Set background
18) feh --bg-scale /path/to/image.png (pay attention to include the *full* path, not ~)
19) add "$ ~/.fehbg &" to .xinitrc
