Tiny Arch
---------

Tiny Arch generates a 10M bootable iso with pacman. The iso generated is
minimal, just some drivers, busybox commands and pacman.

# How to use

Install the package:

```sh
mkdir -p /var/abs/local
cd /var/abs/local
wget https://github.com/hackaugusto/tinyarch/archive/master.zip -O tinyarch.zip
unzip tinyarch.zip
rm tinyarch.zip
cd tinyarch-master
makepkg
# [sudo] pacman -U tinyarch-1-1-x86_64.pkg.tar.xz
```

After the install run `tinyarch container` to create the iso.

To use the image with qemu (using virtio, by default the module
for e1000 is not inserted in the image):

```sh
qemu-system-x86_64 -device virtio-net,netdev=network0 -netdev user,id=network0 -boot order=d -cdrom tinyarch.iso
```

# Configuration

Inform additional packages to install in the container in the command line
`tinyarch container {packages}`.

Change the configuration file `/etc/mkinitcpio-tinyarch.conf` to add new
`FILES` or `MODULES` in the image (the files and modules are copied from
the container not the host)

# How it works

The script will `pacstrap` a base system in a temporary folder, copy itself
into this base system and run using `systemd-nspawn` to create the iso. The
bootloader is syslinux, the kernel is arch's stock, the iso filesystem is
clean and all the binaries are in the initramfs, including pacman.

## Boot

Tiny Arch generates an iso image using xorriso, xorriso suports el torito for
setting up the boot loader. The image generated by Tiny Arch will use syslinux
as it bootload.
