# btrfs-swapon

Btrfs doesn't allow to swap on a file. This script allows you do swap on a file anyway. 

Keep in mind, that a copy-on-write file system is not the best choice to use a swap file. Don't expect high performance.  


This script is based on http://www.spinics.net/lists/linux-btrfs/msg28533.html
and https://gist.github.com/romaninsh/118952ce61643914fb00

## Usage

```
Usage: btrfs-swapon <size> <file>
       btrfs-swapoff <file>

size:      the size of the file, like "8G"
file:      path to the swap file.
```

## Using the systemd service
#### Installing (run manually)
```
cp btrfs-swapoff btrfs-swapon /sbin/
cp btrfs-swapon.service /etc/systemd/system/
```

#### executing systemctl
```
systemctl start btrfs-swapon.service
systemctl stop btrfs-swapon.service
```
#### and check:
```
free -hw
```

## Enable/disable service auto-start (run at boot)
#### enable:
```
systemctl enable btrfs-swapon.service
```
#### disable:
```
systemctl disable btrfs-swapon.service
```
#### and check:
```
systemctl is-enabled btrfs-swapon.service
free -hw
```

## WARNNG
Don't balance your file system as long as you use this swap file.
SWAP creating service will start at boot after syslog - "After=syslog.target".
You may use additional folder for swapfile like "/swap" with btrfs option "chattr -R +C <folder>" to disable BTRFS COW (copy-on-write) for this folder.
