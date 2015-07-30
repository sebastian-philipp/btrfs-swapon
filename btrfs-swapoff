#!/bin/sh
#
# Copyright (C) Sebastian Philipp
#
# roughly based on https://gist.github.com/romaninsh/118952ce61643914fb00 (Set up swap on CoreOS)
#

set -e

swapname="$1"
swapfile="$(losetup -j "$swapname" | /usr/bin/cut -d : -f 1)"

if [ -z "$swapname" -o -z "$swapfile" ]
then
	cat <<EOF
Usage: $0 <file>

file:      path to the existing swap file. This file should have been created with btrfs-swapon.
EOF
	exit 1
fi


swapoff "$swapfile"
losetup -d "$swapfile"
rm "$swapname"
