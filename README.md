1. Expand disk size in virtualization
2. swapoff <swap partition>
3. unmount -a  (unmount all mouting points)
4. sudo fdisk </dev/...>
5. run command to print out all existing partitions, not start sector of the main partition to expand
6. delete all partitions 
7. create new partition, focus on primary partition first, ensure start sector same as before
	***** can use function +<size>G for last sector 
8. create new partition for swap 
9. tongle bootable on primary partition 
10. mkswap </dev/...> partition for swap 
11. run swapon </dev/...> swap partition
12. run blkid - find UUID of swap partition
13. edit /etc/fstab to mount swap partition permenantly
14. run resize2fs /dev/sdaX to adjust partition to assume all free space 