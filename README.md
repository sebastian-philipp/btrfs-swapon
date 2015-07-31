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
#### Installing
```
cp btrfs-swapoff btrfs-swapon /sbin/
cp btrfs-swapon.service /etc/systemd/system/
```

#### executing systemctl
```
systemctl start btrfs-swapon.service
systemctl stop btrfs-swapon.service
```

## WARNNG
Don't balance your file system as long as you use this swap file. 

