# Sysadmin Tools

## Networking

```shell
sudo apt install whois net-tools
```

## [LVM tools](https://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

![LVM Cheatsheet](https://www.howtogeek.com/wp-content/uploads/2011/01/lvm-cheatsheet.png)

Take a look at what's going on

```shell
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
sudo lvs
```

[Extend lvm swap partition](https://www.2daygeek.com/how-to-create-extend-swap-partition-in-linux-using-lvm)

```shell
sudo lvdisplay
SWAP=/dev/ubuntu-vg/swap_1
sudo swapoff -v $SWAP
sudo lvresize $SWAP -L 32G
sudo mkswap $SWAP
sudo swapon -va
free -g
```

[Shrink lvm](https://www.rootusers.com/lvm-resize-how-to-decrease-an-lvm-partition/) to allow space for targetted volumes, snapshots:

```
# reboot to live cd to umount root...
DEV=/dev/centos/var
VG=/dev/vg/disk-name

umount $DEV
e2fsck -fy $DEV
resize2fs $DEV 200G
lvreduce -L 5G $VG
resize2fs $DEV
mount $DEV /mnt/foo
```

Ideas:
Special lv for db snapshots...
Take snapshots...
Second linux os's


**TODO**

* backup state (online)
* set desktop photos
