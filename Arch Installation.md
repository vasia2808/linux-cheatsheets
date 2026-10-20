# Arch Installation

### Connect to the internet

```bash
iwctl --passphrase ryangosling station wlan0 connect Bulo4ki
```

### Partition the disks

The first partition: 512MB, type - 1 EFI System;
The second partition: the rest of the space.

```bash
fdisk -l
fdisk /dev/sda
```

### Mount the file systems

```
mount /dev/sda2 /mnt
mount --mkdir /dev/sda1 /mnt/boot
```

### Install essential packages

```
pacstrap -K /mnt base linux linux-firmware grub efibootmgr sudo networkmanager intel-ucode neovim
```

### Generate fstab

```
genfstab -U /mnt >> /mnt/etc/fstab
```

### Change root into the new system

```
arch-chroot -S /mnt
```

