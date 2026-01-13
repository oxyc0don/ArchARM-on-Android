# ArchARM-on-Android
ArchARM on Android

### Prepare
##### ToDo: remove systemd & install busybox
```
Get Generic AArch64 tarball:
wget http://os.archlinuxarm.org/os/ArchLinuxARM-aarch64-latest.tar.gz

create folder:
mkdir archarm

extract as root (noot sudo):
bsdtar -xpf ArchLinuxARM-aarch64-latest.tar.gz -C archarm

mount -t proc proc archarm/proc/
mount -t sysfs sys archarm/sys/
mount -o bind /dev archarm/dev/

chroot archarm/ /bin/bash

ToDo: remove systemd & install busybox

```

### On Android
```
mkdir -p /data/local/arch/arm64
ARCHDIR="/data/local/arch/arm64"

wget http://os.archlinuxarm.org/os/ArchLinuxARM-aarch64-latest.tar.gz
tar -xvzf ArchLinuxARM-aarch64-latest.tar.gz -C ${ARCHDIR}/

mount -t proc proc ${ARCHDIR}/proc/
mount -t sysfs sys ${ARCHDIR}/sys/
mount -o bind /dev ${ARCHDIR}/dev/

# due to lack of landlock kernel module we need to uncommen #DisableSandbox in pacman.conf
cp -r pacman.conf ${ARCHDIR}/etc/pacman.conf

# define a dns in resolv.conf
rm ${ARCHDIR}/etc/etc/resolv.conf
cp resolv.conf ${ARCHDIR}/etc/etc/resolv.conf



chroot  ${ARCHDIR} /bin/bash


umount ${ARCHDIR}/proc
umount ${ARCHDIR}/sys
umount ${ARCHDIR}/dev



```
