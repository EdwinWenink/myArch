# Installing OpenSSH and generating keys

Information on ssh keys and configs are stored in /etc/ssh/

* pacman -S openssh
* ssh-keygen
* eval \$(ssh-agent)
* ssh-add
* ssh-copy-id remotename@remotehostaddress

On remote server: authorized keys stored in ~/.ssh/authorized_keys
ssh & sshd configuration files stored in /etc/ssh/
In configuration files, commented lines are default values

# for passwordless login
- disable password login, disable root login, enable X11 forwarding for graphical applications if desired
- in sshd_config, pay attention that the correct path for AuthorizedKey is given. Reference to home directory cannot be ~, but needs to be called with path variable %h instead...
- ssh is denied if the rights on ~, ~/.ssh, ~/.ssh/authorized_keys are not strict enough

# Find IP-addresses
ip addr show

# Port forwarding setup on VirtualBox guest:

In VirtualBox the default NAT setting is not enough. Either use port forwarding or expose VirtualBox to internet with bridged network.

- Determine custom port your server listens to
- In VBox, add port forward from a port on the host to the chosen port on the guest you listen to
- Add port forwarding of the physical router to your chosen host port
: internet --> router --> host port --> virtual guest port

