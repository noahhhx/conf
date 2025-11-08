# Jellyfin

## WSL Setup
On WSL (or just server host) create directories:
- /home/noah/jellyfin/config
- /home/noah/jellyfin/cache
- /home/noah/media/
- /home/noah/media2/

On the Windows host create \
`C:\Users\noah\Media\` and sub directories `movies` & `shows` (how I configure jellyfin) \
Then on WSL mount the drive
```sh
sudo mkdir -p /home/noah/media
sudo mount --bind /mnt/c/Users/noah/Media /home/noah/media
```
and share the `C:/Users/noah/Media` folder over the network from Windows if you want to add media from elsewhere.

If WSL restarts, the above mount is lost. You will have to recreate it, make sure to restart the Jellyfin container so it picks it back up.

Or, mount on WSL boot
```shell
sudo nano /etc/wsl.conf
```
```ini
[boot]
command="mount --bind /mnt/c/Users/noah/media /home/noah/media"
```

## Start Jellyfin
Run `docker compose up`.

## Windows Setup

Expose ports on Windows \
Replace 172.20.112.1 with IP of WSL2
```ps
netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=8096 connectaddress=172.20.112.1 connectport=8096
```