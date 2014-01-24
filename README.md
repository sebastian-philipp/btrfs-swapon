Btrfs doesn't allow to swap on a file. This script allows you do swap on a file anyway. 

Keep in mind, that a copy-on-write file system is not the best choice to use a swap file. Don't expect high performance.  


This script is based on http://www.spinics.net/lists/linux-btrfs/msg28533.html
