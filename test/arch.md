# btw

## Install
- Boot into the ISO.
- Basically follow `https://wiki.archlinux.org/title/Archinstall` till we're installed.
  - Choose Hyprland with sddm & make sure your user can use sudo.  
- Restart with the installation device removed.
- You should be able to login as the user you setup & press SUPER+Q to launch a terminal.
- Update your system
  `sudo pacman -Syu`
  if no internet check /etc/resolv.conf for nameserver 8.8.8.8 entry.
- Install git
  `sudo pacman -S git`
- Install the AUR
  ```shell
  git clone https://aur.archlinux.org/yay.git
  cd yay
  makepkg -si
  ```
  `rm -rf ~/yay`
