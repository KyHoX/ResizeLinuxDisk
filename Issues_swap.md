Issue happen when swap disk changed UUID after resize disk.
Error display with message 
    issue of cryptsetup: ERROR: Couldn't resolve device in Kali 
To solve issue, we need to check following files

1. turn swap off
    sudo swapoff /dev/sdX
2. Check UUID of your disks
    sudo blkid | grep swap 
	sudo lsblk | grep swap 
3. Check and correct UUID in following files
    /etc/fstab 
	/etc/initramfs-tools/conf.d/resume
	/etc/crypttab
	/etc/default/grub 
4. regenerate initramfs 
	sudo update-initramfs -u
5. turn swap on
	sudo swapon --all -verbose 
6. Check swap info 
    sudo free -h

You can reboot or try to update and upgrade to verify the issue is resolved.