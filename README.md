# ArchARM-on-Android
ArchARM on Android

### Prepare
```
Get Generic AArch64 tarball:
wget http://os.archlinuxarm.org/os/ArchLinuxARM-aarch64-latest.tar.gz

create folder:
mkdir mountpoint

extract as root (noot sudo):
bsdtar -xpf ArchLinuxARM-aarch64-latest.tar.gz -C mountpoint

```

### On Android
```
mkdir -p /data/local/arch/arm64
ARCHDIR="/data/local/arch/arm64"

wget http://os.archlinuxarm.org/os/ArchLinuxARM-aarch64-latest.tar.gz
bsdtar -xpf ArchLinuxARM-aarch64-latest.tar.gz -C ${ARCHDIR}/

mount -t proc proc ${ARCHDIR}/proc/
mount -t sysfs sys ${ARCHDIR}/sys/
mount -o bind /dev ${ARCHDIR}/dev/

chroot  ${ARCHDIR} /bin/bash
```
