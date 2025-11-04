# Home Server

Due to jank explained here https://github.com/noahhhx/usb-hid-relay, the 'server' pc currently runs
Windows and uses WSL for then for hosting other services.

## Headless Windows
- Make use of a [dummy hdmi plug](https://www.amazon.co.uk/dp/B087QDCZ4L) to allow remote in without 
display connected.
- Enable auto-login using netplwiz

## WSL
Install and setup a WSL instance... then set WSL to startup with Windows
- Change default terminal profile to launch wsl: `C:\WIDNOWS\System32\wsl.exe -d Ubuntu`
- Start terminal on Windows startup.
- Install Docker https://docs.docker.com/engine/install/ubuntu/
  - Make sure to follow post install steps
- Install Portainer https://docs.portainer.io/start/install-ce/server/docker/linux
- Update firewall settings to allow traffic through on local network.
  - Find WSL IP `wsl hostname -I`
  - Windows LAN IP `ipconfig`
  - Set up portforwarding `netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=9000 connectaddress=172.20.112.1 connectport=9000` replace 172.xxx with WSL IP and 9000 with portainers port.
  - Ensure private network is enabled in the Windows 11 network settings.
- We should now be able to access Portainer (and other containers using above technique) on any other device
 in the network. `https://192.168.0.26:9443`