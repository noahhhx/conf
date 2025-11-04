# Jellyfin
On WSL (or just server host) create directories:
- /home/noah/jellyfin/config
- /home/noah/jellyfin/cache
- /home/noah/media/

Run `docker compose up`.

Expose ports on Windows \
Replace 172.20.112.1 with IP of WSL2
```ps
netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=8096 connectaddress=172.20.112.1 connectport=8096
```

On the Windows host create \
`C:\Users\noah\Media\` and sub directories `movies` & `shows` (how I configure jellyfin) \
Then on WSL mount the drive
```sh
sudo mkdir -p /home/noah/media
sudo mount --bind /mnt/c/Media /home/noah/media
```
and share the `C:/Users/noah/Media` folder over the network from Windows if you want to add media from elsewhere.
