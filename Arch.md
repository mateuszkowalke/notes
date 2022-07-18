# Arch

### Installation

The proper way of installing depends on hardware. Make sure to use proper combination of efi/boot booting and gpt/dos partition tables.

Remember to install vim and iwd (for wifi connectivity). For wifi to work correctly we have to enable three services:
```
systemctl enable --now iwd
systemctl enable --now systemd-resolved
systemctl enable --now systemd-networkd
```
To configure dns:
```
ln -rsf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
```
To configure networkd create /etc/systemd/network/25-wireless.network:
```
[Match]
Name=wlp2s0

[Network]
DHCP=yes
IgnoreCarrierLoss=3s
```

To create user we need sudo package. Then we enable wheel group:
```
EDITOR=vim visudo
```
And create user:
```
useradd -G wheel -m <name> -p <password>
```

Update and upgrade:
```pacman -Syu```

Install dwm, st and dmenu.

First, you will need to install X server and Git (as root)
```
pacman -S xorg-xinit xorg git
```
Change directory to /usr/src because you want this to apply to all users:
```
cd /usr/src
```
As root, clone suckless software such as dwm (window manager), st (recommended terminal), and dmenu (simple application menu)
```
git clone https://git.suckless.org/dwm
git clone https://git.suckless.org/st
git clone https://git.suckless.org/dmenu
```
(if it hangs on cloning into dwm..., then probably we need to reduce MTU: 
``` echo 1000 > /sys/class/net/wlan2/mtu) ```
Install make, gcc and base-devel packages.
Change directory into each one, and compile them:
```
cd dwm ## Do this step also with st and dmenu
sudo make clean install
```
Add a new user to the users group (as root):
```
usermod -G users <user>
```
Log out, log in as new user, and execute:
```
<favorite text editor> .xinitrc
```
    from there, add "exec dwm" into the file, save, and exit
Add "exec dwm", save and exit.
Start your session with:
```
startx
```
Install utility programs:
```
pacman -S curl wget
```
